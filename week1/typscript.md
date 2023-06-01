# Typescript

## REPL(Read-Eval-Print-Loop)

터미널에서 간단하게 REPL을 쓰고 싶으면
ts-node를 사용하면 된다.

```bash
npx ts-node
```

## Interface vs Type

Interface와 Type Alias 다소 비슷해보이는 것은 사실이나
사용자 정의 타입이 할 수 없는 것을 인터페이스는 할 수 있다.
할 수 있는 것 중 하나는 인터페이스는 `선언을 병합`할 수 있다는 점이다.

아래의 타입들은 내가 현재 실무에서 사용하고 있는 프로모션 타입들 중 일부분을 가져왔다.

### Interface

인터페이스는 명시적으로 확장을 사용해서 정의를 해줄 수도 있다.

```typescript
export interface PromotionCoupon {
  promoId: string,
  name: string,
  issuanceType: PromotionIssuance,
  createdAt: string,
  expiryAt: string,
  code: string,
  discountType: PromotionDiscount,
  discountRate: number,
}

export interface PromotionCouponList extends PromotionCoupon {
  targetCount: number,
  issuanceCount: number,
}
```

또 Type Alias에서 하지 못하는 `선언 병합`을 할 수 있다.

```typescript
interface ButtonInterface {
  onInit():void;
  onClick():void;
}

...

interface ButtonInterface {
  onToggle():void;
}
```

위와 같이 선언 되었을 때 인터페이스는 오류가 나지 않는다.

### Type

타입은 병합하고자 하는 타입과 & 기호를 활용해서 타입 병합이 가능하다.

```typescript
export type PromotionOwnerList = {
  uuid: string,
  email: string,
  nickname: string,
  userPromoStatusId: string,
  promoId: string,
  maxUseAt: string,
  usedAt: string | null,
  isUsed: boolean,
  createdAt: string,
  isChecked?: boolean,
}

export type PromotionCandidateList = User & {
  provider: Provider,
  emailCert: boolean,
  privacyAgree: boolean,
  eventAgree: boolean,
  createdAt: string,
  isChecked?: boolean,
}
```

```typescript
type ButtonType = {
  onInit():void;
  onClick():void;
}

// [오류]
// 'ButtonType' 식별자가 중복되었다.
type ButtonType = {
  onToggle():void;
}
```

타입에서는 오류가 발생한다.

## 타입 추론과 타입 단언

### 타입 추론

```javascript
let x = 3;

let y = 'hello';
```

위와 같이 `x`에 대한 타입을 지정하지 않더라도 `number`타입으로
`y`에 대한 타입을 지정하지 않더라도 `string`타입으로 간주된다.

### 타입 단언

```javascript
let assertion:any = "타입 어설션은 '타입을 단언'한다.";

// 방법 1: assertion 변수의 타입을 string으로 단언 처리
let assertion_count:number = (<string>assertion).length;
```

```javascript
let assertion:any = "타입 어설션은 '타입을 단언'한다.";

// 방법 2: assertion 변수의 타입을 string으로 단언 처리
let assertion_count:number = (assertion as string).length;
```

{% hint style="info" %}
 두 방법 모두 결과는 동일하다. 하지만 JSX와 함께 사용하는 경우에는 as 문법만 허용된다.
{% endhint %}

보통 JSX에서 많이 쓰는 타입 단언에는 div태그에서 이벤트가 발생한 상태에서 해당 div안의 input에서
값을 가져와야 하는 경우에 타입 단언을 많이 사용했다.

```typescript
  const onChangeCategory = useCallback((e: React.FormEvent<HTMLDivElement>) => {
    const { value } = (e.target as HTMLInputElement);
    ...
  }, []);
```

## Union Type vs Intersection Type

### Union Type

유니온 타입(Union Type)은 A이거나 B이다 라는 의미의 타입이다.

보통 지정된 값 이외의 값이 들어가지 않아야 할 때 유니온 타입을 지정해서 많이 사용하는 편이다.

```typescript
export type PromotionCategory = 'COUPON' | 'LINK';
export type PromotionDiscount = 'FREE' | 'DISCOUNT';
```

### Intersection Type

인터섹션 타입(Intersection Type)은 여러 타입을 모두 만족하는 하나의 타입이다.

```typescript
export type PromotionCandidateList = User & {
  provider: Provider,
  emailCert: boolean,
  privacyAgree: boolean,
  eventAgree: boolean,
  createdAt: string,
  isChecked?: boolean,
}
```

```typescript
interface Person {
  name: string;
  age: number;
}
interface Developer {
  name: string;
  skill: number;
}
type Capt = Person & Developer;
```

## Optional Parameter

JavaScript에서는 존재하지 않는 프로퍼티에 접근하였을 때, 런타임 오류가 발생하지 않고
undefined 값을 얻게 된다.

```typescript
export type PromotionCandidateList = User & {
  provider: Provider,
  emailCert: boolean,
  privacyAgree: boolean,
  eventAgree: boolean,
  createdAt: string,
  isChecked?: boolean, <- option
}
```

```typescript
function printName(obj: { first: string; last?: string }) {
  // ...
}
// 둘 다 OK
printName({ first: "Bob" });
printName({ first: "Alice", last: "Alisson" });
```

### References

- [typescript 공식문서](https://www.typescriptlang.org/docs/handbook/intro.html)
- [yamoo9.gitbook.io](https://yamoo9.gitbook.io/typescript/interface)
- [joshua1988.github.io](https://joshua1988.github.io/ts/guide/type-inference.html)
