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

<img width="1338" height="784" alt="Image" src="https://github.com/user-attachments/assets/d93520d8-d3f3-4d1e-8122-908c1bf20e94" />

만들어둔 애니메이션을 적용시키기 위하여, “BP_Player”를 열어준 이후, 디테일 탭에서 애님 클래스를 위에서 작성한 ABP_Player로 변경하면 애니메이션이 적용된다.

>## 게임 UI

### **Widget Blueprint** 

**Widget Blueprint**는 언리얼 엔진에서 **UI(User Interface)를 시각적으로 설계하고 구현**하는 도구로,

이를 사용해 **버튼, 슬라이더, 텍스트**와 같은 다양한 위젯을 조합하여 게임의 인터페이스를 만드는 것이 가능하다.

또한, **UI 요소와 게임 로직을 연결**해 사용자 입력에 반응하거나 데이터를 표시하는 등 **동적인 UI**를 구현할 수 있다.

>### **Widget Blueprint의 특징과 활용**

1. **시각적 UI 설계 도구**
    - **Widget Blueprint**는 드래그 앤 드롭 방식으로 UI를 손쉽게 설계할 수 있는 도구이다.
    - **버튼, 텍스트, 슬라이더, 이미지** 등 다양한 위젯을 제공하며, 이를 조합해 **메뉴, HUD, 인벤토리 시스템** 등을 제작할 수 있다.
2. **Blueprint Event Graph를 통한 로직 구현**
    - Widget Blueprint는 이벤트 그래프를 통해 **게임 로직과 UI 상호작용**을 구현할 수 있다.
    - 예를 들어, 버튼 클릭 시 게임을 일시정지하거나, 체력 수치를 텍스트로 표시할 수 있다.
3. **데이터 바인딩**
    - Widget Blueprint는 **데이터 바인딩**을 통해 실시간으로 UI를 갱신하는 것이 가능하다. 게임 내 값(예: 플레이어 체력)이 변경될 때 UI도 자동으로 업데이트할 수 있다.

>### **Widget Blueprint  화면구성**

**위젯 구성 요소 추가**

- **Canvas Panel**: UI 요소를 배치할 수 있는 기본 패널, 다른 위젯을 이 패널에 배치한다.
- **버튼, 텍스트, 이미지 등 추가**: 다양한 위젯을 드래그해 **Canvas Panel**에 배치할 수 있다.


>### **기본적인 게임 UI 만들기**

1. **C++ Widget Class 생성** : 상단 툴 → 새로운 C++ 클래스 선택,  [ 모든 클래스 ] 를 선택 한 뒤, UserWidget을 부모 클래스로 선택한 다음, “MainHud”로 이름을 설정 한 뒤, 클래스를 생성해준다.

**MainHud.h**

```cpp
#pragma once

#include "CoreMinimal.h"
#include "Blueprint/UserWidget.h"
#include "MainHud.generated.h"

UCLASS()
class BASIS_API UMainHud : public UUserWidget
{
	GENERATED_BODY()
	
public:
	UPROPERTY(meta = (BindWidget))
	TObjectPtr<class UProgressBar> HPGauge;

	UPROPERTY(meta = (BindWidget))
	TObjectPtr<class UTextBlock> HPPercent;

	UPROPERTY(meta = (BindWidget))
	TObjectPtr<class UTextBlock> KC;

	UPROPERTY(meta = (BindWidget))
	TObjectPtr<class UTextBlock> SC;

	UFUNCTION()
	void SetHP(float Value);

	UFUNCTION()
	void SetKillCount(int32 Value);	

	UFUNCTION()
	void SetStageCount(int32 Value);
};


```

- 변수 위에 UPROPERTY(meta = (BindWidget)) meta 선언 시, **UI 상에 변수명과 동일한 위젯이 존재하는 경우, 자동으로 바인딩 해준다**

**MainHud.cpp**

```cpp

#include "MainHud.h"
#include "Components/ProgressBar.h"
#include "Components/TextBlock.h"

void UMainHud::SetHP(float Value)
{
	if(IsValid(HPGauge))
	{
		HPGauge->SetPercent(Value);
	}
	if(IsValid(HPPercent))
	{
		int32 Hp = Value * 100;
		FText Text = FText::FromString(FString::Printf(TEXT("%d"), Hp));
		HPPercent->SetText(Text);
	}

}

void UMainHud::SetKillCount(int32 Value)
{
	if(IsValid(KC))
	{
		FText Text = FText::FromString(FString::Printf(TEXT("KillCount: %d"), Value));
		KC->SetText(Text);
	}
}

void UMainHud::SetStageCount(int32 Value)
{
	if (IsValid(SC))
	{
		FText Text = FText::FromString(FString::Printf(TEXT("Stage: %d"), Value));
		SC->SetText(Text);
	}
}


```
2. 콘텐츠 브라우저에서 **마우스 우클릭** 후 **블루프린트 -> 블루프린트 클래스를** 선택한 이후, 방금 생성한 “MainHud”를 부모 클래스로 선택하여 MainHud Blueprint를 생성한다.
- 이 “MainHud”를 플레이어 화면에 띄우기 위해 GameMode를 만들어 게임이 시작될 때 MainHud를 불러오고 실시간으로 업데이트 해준다.
   
3. **C++ GameMode 생성** : 상단 툴 → 새로운 C++ 클래스 선택,  [ 모든 클래스 ] 를 선택 한 뒤, GameMode를 부모 클래스로 선택한 다음, “MainHud”로 이름을 설정 한 뒤, 클래스를 생성해준다.

 **MainGameMode.h**

```cpp
#pragma once

#include "CoreMinimal.h"
#include "GameFramework/GameMode.h"
#include "MainGameMode.generated.h"

UCLASS()
class BASIS_API AMainGameMode : public AGameMode
{
	GENERATED_BODY()
public:
	virtual void BeginPlay() override;
	virtual void Tick(float DeltaSeconds) override;

	UPROPERTY(EditAnyWhere)
	TSubclassOf<class UUserWidget> WidgetClass;

	UPROPERTY()
	TObjectPtr<class UUserWidget> Widget;

	int32 Stage;
	int32 KillCount;
	float HP;
};


```

**MainGameMode.h**

```cpp

#include "MainGameMode.h"
#include "Blueprint/UserWidget.h"
#include "PlayerBase.h"
#include "MainHud.h"

void AMainGameMode::BeginPlay()
{
	Super::BeginPlay();
	if (IsValid(WidgetClass))
	{
		Widget = CreateWidget<UUserWidget>(GetWorld(), WidgetClass);
	}
	if (Widget)
	{
		Widget->AddToViewport();
	}
	Stage = 0;
}

void AMainGameMode::Tick(float DeltaSeconds)
{
	UWorld* World = GetWorld();
	if (!IsValid(World))
	{
		return;
	}
	APlayerController* PC = World->GetFirstPlayerController();
	if (!IsValid(PC))
	{
		return;
	}
	APlayerBase* PB = Cast<APlayerBase>(PC->GetPawn());
	if (!IsValid(PB))
	{
		return;
	}

	HP = (float)(PB->CurrentHP) / PB->FullHP;

	KillCount = PB->KillCount;

	UMainHud* Hud = Cast<UMainHud>(Widget);

	if(!IsValid(Hud))
	{
		return;
	}

	Hud->SetHP(HP);
	Hud->SetKillCount(KillCount);
	Hud->SetStageCount(Stage);
}

```

4. 콘텐츠 브라우저에서 **마우스 우클릭** 후 **블루프린트 -> 블루프린트 클래스를** 선택한 이후, 방금 생성한 “MainGameMode”을 부모 클래스로 선택하여 GameMode Blueprint를 생성한다.

5. GameMode Blueprint에서 Widget Class에 방금 만든 MainHud Blueprint를 넣고, 저장한다.
6. 프로젝트 설정에서 MainGameMode Blueprint를 기본 게임모드를 설정하면 게임 플레이시 MainHud가 정상적으로 작동하게 된다.
 
## 3. 내일 학습 할 것은 무엇인지

쉽게 배우는 C++ 언리얼 엔진 3D 게임 개발 기초 4주차의 AI 만들기와 기존 블루 프린트 노드 작업을 

다시 코드로 변환하는 강의를 들으면서 AI를 만들때 필요한 C++ 코딩 방법을 공부할 예정이다.

#내일배움캠프 #사전캠프 #TIL 
