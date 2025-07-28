# [내일배움캠프 사전캠프] + 쉽게 배우는 C++ 언리얼 엔진 3D 게임 개발 기초 3주차

## 1. 오늘 학습 키워드

>## 캐릭터 애니메이션 제어

### 애니메이션 에셋

### 애니메이션 블렌딩

### 애니메이션 블루프린트를 통한 애니메이션 제어

>## 게임 UI

### Widget Blueprint 

## 2. 오늘 학습 한 내용을 나만의 언어로 정리하기

>## 캐릭터 애니메이션 제어

### **애니메이션 에셋**

애니메이션 에셋에는 여러 가지 종류가 있는데,

그 중에서 대표적으로 사용되고 있는것이 3개가 있다.

애니메이션 시퀀스, 애니메이션 몽타주, 그리고 애님 블루프린트이다. 

### 1. 애니메이션 시퀸스(Animation Sequence)

애니메이션 시퀀스는 **가장 기본적인 애니메이션 에셋**입니다. 

3DMax나 Blender 같은 외부 툴을 이용하여, 애니메이션 파일을 Import(추가) 하여 생성한다. 

애니메이션 시퀸스는 캐릭터가 특정 동작을 시간에 따라 반복하도록 만들어진 파일로,

예를 들어, 걷기 애니메이션, 뛰기 애니메이션 같은 것들이 여기에 해당한다.

이 시퀀스는 루프(loop)가 가능해, 걷는 동작을 무한히 반복하게 할 수도 있고, 특정 시간 동안만 실행되도록 설정하는게 가능하다.

### 2. 애니메이션 몽타주(Animation Montage)

애니메이션 몽타주는 **여러 애니메이션 시퀀스를 조합하여 복잡한 동작을 구현하는 에셋**이다.

몽타주는 주로 특수한 상황에서 사용되며, 다양한 애니메이션을 하나의 흐름으로 연결하는 역할을 맡고 있다.

대표적인 예로 캐릭터 연속적인 콤보 공격이 애니메이션 몽타주를 활용하여 표현할 수 있습니다. 

각각의 공격 동작을 애니메이션 시퀀스로 만들고 이를 자연스럽게 연결하여 **하나의 연속된 동작**으로 만들어주는 것이 가능하게 해준다.

### 3. 애님 블루프린트 (Anim Blueprint)

애님 블루프린트는 **캐릭터의 애니메이션 동작을 제어하는 로직을 정의하는 에셋**이다.

이 블루프린트는 단순히 애니메이션 시퀀스를 재생하는 것에 그치지 않고,

**캐릭터의 상태나 행동에 따라 적절한 애니메이션을 실시간으로 전환하고 제어하는 기능**을 제공한다.

애님 블루프린트는 **상태 머신**(State Machine)을 통해 캐릭터의 상태에 맞는 애니메이션을 결정하고, 애니메이션 간의 자연스러운 전환을 관리하는 것이 가능하다.

예를 들어, 캐릭터가 걷다가 뛰기 동작으로 전환하거나, 점프 후 착지하는 등의 다양한 상황을 애님 블루프린트에서 제어할 수 있고, 수정하기 매우 편하다.

상태 머신에서는 캐릭터의 현재 상태(걷기, 뛰기, 점프 등)를 기준으로 애니메이션을 선택하고, 조건에 따라 상태를 전환하게 만들 수 있다.

### **애니메이션 블렌딩**

애니메이션 블렌딩은 **여러 애니메이션을 부드럽게 연결하여 자연스러운 동작을 구현하는 기술**이다.

게임 내 캐릭터가 다양한 상황에서 여러 동작을 수행할 때, 이 동작들이 갑작스럽게 전환되면 어색해 보일 수 있다.

이를 방지하고 애니메이션 간의 전환이 매끄럽게 이루어지도록 돕는 것이 바로 애니메이션 블렌딩이다.

예를 들어서 캐릭터가 서있는 상태에서 걷기 시작하는 동작, 뛰는 동작을 부드럽게 연결해주는 역할을 한다.

### 1. 블렌드 스페이스(Blend Space)

블렌드 스페이스(Blend Space)는 **여러 애니메이션을 특정 변수를 기준으로 자연스럽게 섞어주는 기능**이다.

게임에서 캐릭터가 한 동작에서 다른 동작으로 부드럽게 전환할 때, 갑작스럽게 애니메이션이 바뀌면 어색해 보일 수 있는데,

블렌드 스페이스는 이런 문제를 해결하는 데 제작자한테 큰 도움을 준다.

예를 들어, 캐릭터의 이동 속도가 0 일 때는, 캐릭터가 가만히 서있는 상태로 유지되게 하고,

이동 속도가 0보다 커진 경우에는 걷는 모션을 보여줄 수 있게 만들 수 있다.

### 2. 레이어드 블렌딩(Layered Animation Blending)

레이어드 블렌딩은 **캐릭터의 특정 부분에만 애니메이션을 적용하거나,**

혹은 **서로 다른 애니메이션을 결합하여 캐릭터가 복합적인 동작을 수행하도록 하는 기능**이다.

즉, 캐릭터의 상체와 하체에 각각 다른 애니메이션을 적용하는 방식이라 할 수 있다.

이 기능을 사용하면 캐릭터가 여러 동작을 동시에 수행할 수 있어, 더욱 다채롭고 자연스러운 움직임을 구현할 수 있게 된다.

예를 들어 하체는 달리기를 하는 동작, 상체는 총을 쏘는 모션을 레이어드 블렌딩으로 구현할 수 있다.

### 애니메이션 블루프린트를 통한 애니메이션 제어

### 1. C++ AnimInstance 생성하기 

1. 콘텐츠 브라우저에서 C++클래스 폴더를 선택한 이후, 우클릭하여 새 C++ 클래스를 클릭한 다음,

2. 모든 클래스를 선택한 뒤, “AnimInstance”를 검색하여 찾아서 선택한다.

3. 그리고 파일명을 “MainAnimInstnace”으로 적어주고, “클래스 생성” 버튼을 눌러주면 C++ AnimInstance 생성하기가 완료된다.

>### MainAnimInstance.h

```cpp
#pragma once

#include "CoreMinimal.h"
#include "Animation/AnimInstance.h"
#include "MainAnimInstance.generated.h"

/**
 * 
 */
UCLASS()
class LECTURE1_API UMainAnimInstance : public UAnimInstance
{
	GENERATED_BODY()

public:
	virtual void NativeInitializeAnimation() override;
	virtual void NativeUpdateAnimation(float DeltaSeconds) override;

	UFUNCTION()
	void AnimNotify_Attack();

	UPROPERTY(BlueprintReadOnly)
	TObjectPtr<class ACharacter> Character;

	UPROPERTY(BlueprintReadOnly)
	TObjectPtr<class UCharacterMovementComponent> MovementComponent;

	UPROPERTY(BlueprintReadOnly)
	float Speed;
};

```

>### MainAnimInstance.cpp

```cpp
#include "MainAnimInstance.h"
#include "GameFramework/Character.h"
#include "MathUtil.h"
#include "GameFramework/CharacterMovementComponent.h"

void UMainAnimInstance::NativeInitializeAnimation()
{
	Super::NativeInitializeAnimation();

	Character = Cast<ACharacter>(TryGetPawnOwner());
	if (IsValid(Character))
	{
		MovementComponent = Character->GetCharacterMovement();
	}
}

void UMainAnimInstance::NativeUpdateAnimation(float DeltaSeconds)
{
	Super::NativeUpdateAnimation(DeltaSeconds);

	if (IsValid(MovementComponent))
	{
		Speed = MovementComponent->Velocity.Size();
	}
}

void UMainAnimInstance::AnimNotify_Attack()
{
	//공격시에 처리할 내용.
}

```

- NativeInitializeAnimation : 코드가 최초 실행 될 때, 1번만 호출되는 함수로 애니메이션과 관련된 초기 설정을 하는 함수. TryGetPawnOwer를 통하여, ACharacter와 UCharacterMovementComponent를 미리 저장해둘 수 있다.
- NativeUpdateAnimation : 매 프레임마다 업데이트되는 함수로, 애니메이션의 상태를 실시간으로 업데이트한다. 캐릭터의 이동속도를 가져오는 역할을 수행한다.
- AnimNotify_Attack : 캐릭터가 공격해 애니메이션이 재생되면, 애니메이션에서 호출하는 함수

### 2.애니메이션 블루프린트 생성하기 

콘텐츠/Blueprints/Characters 경로 안에 우클릭하여 애니메이션/애니메이션 블루프린트를 선택하고,

Walking_Skeleton 모델을 선택한 이후, C++로 만들어둔 MainAnimInstnace를 부모 클래스로 선택하여 애니메이션 블루프린트를 생성한다.

다음에 파일명을 ABP_Player로 지어준 이후, 파일을 열어주고,

결과 노드에 재생될 애니메이션 시퀀스 혹은 블렌드 스페이스 등을 연결해준다. 이 때, 기존에 생성한 변수인 Speed를 불러올 수 있다.

만들어둔 애니메이션을 적용시키기 위하여, “BP_Player”를 열어준 이후, 디테일 탭에서 애님 클래스를 위에서 작성한 ABP_Player로 변경하면 애니메이션이 적용된다.

>## 게임 UI

### Widget Blueprint 

## 3. 내일 학습 할 것은 무엇인지

쉽게 배우는 C++ 언리얼 엔진 3D 게임 개발 기초 4주차의 AI 만들기와 기존 블루 프린트 노드 작업을 

다시 코드로 변환하는 강의를 들으면서 AI를 만들때 필요한 C++ 코딩 방법을 공부할 예정이다.

#내일배움캠프 #사전캠프 #TIL 
