---
ics: '1'
title: ICS 사양 표준
stage: 초안
category: meta
author: Christopher Goes <cwgoes@tendermint.com>
created: '2019-02-12'
modified: '2019-08-25'
---

## ICS 란 무엇인가?

인터체인 표준(Inter-chain standard, ICS)은 코스모스 생태계 내에서 사용될 수 있는 특정 프로토콜, 표준, 또는 기능들을 설명하는 설계 문서입니다. ICS는 제안하는 표준이 지향하는 특성, 설계 근거 그리고 간결하지만 포괄적인 기술적 사양을 제공해야 합니다. ICS의 주 저자는 프로포절의 표준화 프로세스를 이끌고, 커뮤니티의 지원과 리뷰를 요청하며 적절한 사회적 합의를 위해 관련 이해 관계자와 의사소통을 해야합니다.

인터체인 표준화 프로세스는 생태계 전반의 프로토콜, 변화 그리고 기능을 제안하는 주요 수단이 되어야 합니다. ICS 문서는 합의에 도달한 후에도 향후 구현자가 참고할 수 있도록 설계 결정사항과 정보를 기록해야 합니다.

인터체인 표준은 코스모스 허브와 같은 특정 블록체인의 변경을 제안하거나, 표준의 구현적 특징(특정 언어의 데이터 구조 등) 또는 이미 존재하는 코스모스 블록체인의 거버넌스 프로포절을 논의하기 위해 *사용되어서는 안됩니다* (단, 코스모스 생태계 내 각자 블록체인은 인터체인 표준 도입 여부를 자체 거버넌스 과정을 통해 결정할 수 있습니다).

## 구성 요소

ICS는 헤더, 개요, 명세, 히스토리 로그, 저작권 공시로 구성됩니다. 이 구성 요소는 필수로 작성해야 합니다. 레퍼런스는 링크 형태나, 필요시 하단의 표 형태로 반드시 포함될 수 있습니다.

### 헤더

ICS 헤더는 관련된 메타데이터를 포함합니다.

#### 필수 필드

`ics: #` - ICS 번호 (순차적으로 할당됩니다.)

`title` - ICS 제목 (짧고 명료하게 표현해야 합니다.)

`stage` - 현재 ICS 단계를 나타내며, 사용할 수 있는 단계들은 [PROCESS.md](../../PROCESS.md) 에서 확인할 수 있습니다.

ICS의 승인 단계들에 대한 설명은 [README.md](../../README.md)을 참조하십시오.

`category` - ICS 카테고리, 다음 중 하나입니다:

- `meta` - ICS 절차에 대한 표준
- `IBC/TAO` - 블록체인간 통신 시스템의 전송(transport), 인증(authentication), 순서 정렬(ordering)과 같은 코어 프로토콜에 대한 표준
- `IBC/APP` - 블록체인간 통신 시스템 어플리케이션 레이어 프로토콜에 대한 표준

`author` - ICS 저자 & 연락 정보 (선호 순서 : 이메일, Github, Twitter, 기타 응답을 요구할 수 있는 연락 방법).
제 1 저자는 기본적으로 ICS의 "소유자(owner)"이고, 표준화 과정에 대한 책임을 가지게됩니다. 이후 저자들의 순서는 기여도에 따라 정해져야 합니다.

`created` - ICS 최초 작성 날짜 (`YYYY-MM-DD`)

`modified` - ICS 최근 수정 날짜 (`YYYY-MM-DD`)

#### 선택적 필드

`requires` - 이 표준**이** 요구하거나 의존하는 다른 ICS 표준(번호에 의해 참조됩니다.)

`required-by` - 이 표준**을** 요구하는 다른 ICS 표준 (번호에 의해 참조됩니다.)

`replaces` - 해당되는 경우, 이 표준**으로** 대체되는 다른 ICS 표준

`replaced-by` - 해당되는 경우, 이 표준**을** 대체하는 다른 ICS 표준

### 개요 (Synopsis)

헤더에 이어서, 각 ICS는 제안하는 사양(specification)의 대한 포괄적 설명과 논리적 근거를 제공하는 200자 이내의 간략한 개요를 포함해야 합니다.

### 명세 (Specification)

명세 항목은 ICS의 핵심 구성요소이며 프로토콜 문서, 설계의 논리적 근거, 필요한 레퍼런스 그리고 적절한 기술적 설명을 포함해야 합니다.

#### 하위 구성요소 (Sub-components)

명세는 ICS의 특성에 따라 다음 구성요소 중 일부(또는 모두)가 포함될 수 있습니다. 포함되는 하위 구성요소는 다음과 같은 순서대로 나열돼야 합니다.

- *Motivation(의도)* - 기능 제안에 대한 논리적 근거, 또는 기능 변경 제안에 대한 논리적 근거
- *Definitions(정의)* - ICS 내에서 사용되거나 ICS를 이해하기 위해 필요한 새로운 용어 또는 개념 목록. 최상위 `docs` 폴더에서 정의되지 않은 용어는 이 항목에서 반드시 정의되어야 합니다.
- *Desired Properties(지향하는 속성)* - 명세된 프로토콜 또는 기능이 지향하는 속성(property)과 특성(characteristic)과 해당 속성이 위반되었을 경우 발생하는 결함/효과.
- *Technical Specification(기술적 명세)* - 제안하는 프로토콜의 구문(syntax), 시맨틱(semantics), 하위 프로토콜(sub-protocol), 자료구조(data structures), 알고리즘 그리고 적절한 의사코드(pseudocode)등의 기술적 상세. 기술 명세는 각 서로 인지하지 않는 다수 구현체들이 상호 호환될 수 있을 정도록 자세해야 합니다.
- *Backwards Compatibility(과거 버전 호환성)* - 이전의 기능 또는 프로토콜 버전과의 호환성(또는 비호환성)에 대한 설명
- *Forwards Compatibility(미래 버전 호환성)* - 앞으로 구현할 예정이거나 기대되는 기능, 또는 프로토콜 버전과의 호환성(또는 비호환성)에 대한 설명
- *Example Implementation(구현 예시)* - 구현자들에게 주요 참고 자료로 이용할 수 있는 자세한 구현 예제 또는 설명
- *Other Implementations* - 제작중이거나 완성된 구현체들의 목록(외부 참조)

### 히스토리 (History)

ICS는 히스토리 항목을 포함해야하며, 도움될 수 있는 문서와 중요한 변경 사항에 대한 로그들을 기록합니다.

히스토리 항목의 예제는 [하단](#history-1)을 참조하세요.

### 저작권 (Copyright)

ICS는 [Apache 2.0](https://www.apache.org/licenses/LICENSE-2.0)를 통해 권리를 포기하는 저작권 항목을 포함해야 합니다.

## 서식 (Formatting)

### 일반

ICS 명세는 반드시 GitHub과 호환 가능한 Markdown 으로 작성되어야 합니다.

Github와 호환 가능한 Markdown cheat sheet는 [여기](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)를 참조하세요. 로컬 Markdown 렌더러의 대한 내용은 [여기](https://github.com/joeyespo/grip)를 참조하세요.

### 언어

ICS 명세는 반드시 간단한 영어로 작성되어야 하며, 모호한 용어와 불필요한 전문용어는 지양해야 합니다. 간단한 영어의 좋은 예제는, [Simple English Wikipedia](https://simple.wikipedia.org/wiki/Main_Page)를 참조하세요.

명세의 "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED", "MAY", 그리고 "OPTIONAL"과 같은 단어들은 [RFC 2119](https://tools.ietf.org/html/rfc2119)에 기준에 따라 해석됩니다.

### 의사코드 (Pseudocode)

명세의 의사코드는 언어에 구애받지 않아야 하며, 줄 수, 변수, 간단한 조건문, 반복문, 또는 스케줄링 타임아웃과 같이 기능에 대한 설명이 필요한 부분은 작은 영어 문단으로 표현하는 것과 같이 간단한 표준 형태여야 합니다. LaTeX 이미지는 diff 형태로 리뷰하기 어렵기 때문에 피해야 합니다.

구조체에 대한 의사코드는 간단한 TypeScript를 이용하여, 인터페이스로 작성되어야 합니다.

구조체 의사코드 예제:

```typescript
interface Connection {
  state: ConnectionState
  version: Version
  counterpartyIdentifier: Identifier
  consensusState: ConsensusState
}
```

알고리즘에 대한 의사코드는 간단한 Typescript를 이용하여, 함수로 작성되어야 합니다.

알고리즘 의사코드의 예제:

```typescript
function startRound(round) {
  round_p = round
  step_p = PROPOSE
  if (proposer(h_p, round_p) === p) {
    if (validValue_p !== nil)
      proposal = validValue_p
    else
      proposal = getValue()
    broadcast( {PROPOSAL, h_p, round_p, proposal, validRound} )
  } else
    schedule(onTimeoutPropose(h_p, round_p), timeoutPropose(round_p))
}
```

## 히스토리

이 명세는 Bitcoin의 BIP 프로세스와 Python의 PEP 프로세스에서 파생된 이더리움의 [EIP 1](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-1.md)에서 크게 영감을 얻었습니다. 이전 저자들은 이 ICS 명세나 절차의 부족함에 대해 책임이 없습니다. 모든 코멘트는 ICS 레포지토리 관리자에게 보내주세요.

2019년 3월 4일: 초안 작성 및 PR로 제출
2019년 3월 7일: 초안 병합
2019년 4월 11일: 의사 코드 포맷팅 업데이트, 하위 섹션 정의 추가
2019년 4월 17일: 카테고리 분류

## 저작권

이 문서의 모든 내용은 [Apache 2.0](https://www.apache.org/licenses/LICENSE-2.0)에 따라 라이센스가 부여됩니다.
