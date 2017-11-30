---

copyright:
  years: 2015, 2017
lastupdated: "2017-10-16"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:tip: .tip}
{:pre: .pre}
{:codeblock: .codeblock}
{:screen: .screen}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}

# 인텐트 및 엔티티 플랜
{: #planning-your-entities}

애플리케이션의 *인텐트*를 플랜하려면 고객이 수행할 작업 및 애플리케이션에서 처리할 수 있는 작업을 고려해야 합니다. 사용자 입력의 올바른 인텐트를 선택하는 것이 유용한 응답 제공의 첫 번째 단계입니다. 애플리케이션에 대해 식별하는 인텐트는 작성해야 하는 대화 상자 플로우를 판별합니다. 또한 애플리케이션이 고객 요청을 완료하기 위해 통합해야 하는 백 엔드 시스템(예: 고객 데이터베이스 또는 지불 처리 시스템)을 판별할 수 있습니다.

*엔티티*는 특정 인텐트에 대한 구체적인 컨텍스트 또는 설명을 제공하는 사용자 입력의 용어 또는 오브젝트를 나타냅니다. 인텐트가 동사(사용자가 수행하려는 것)를 나타내면 엔티티는 명사(예: 조치에 대한 컨텍스트 또는 오브젝트)를 나타냅니다. 엔티티를 사용하면 단일 인텐트가 여러 특정 조치를 나타낼 수 있습니다. 엔티티는 클래스의 가능한 오브젝트를 나타내는 특정 값으로 오브젝트의 클래스를 정의합니다.

기본적으로, 요청을 캡처하거나 조치를 수행하려면 인텐트를 사용하십시오. 요청 또는 조치에 응답하는 방법에 영향을 줄 수 있는 정보를 캡처하려는 경우에는 엔티티를 사용하십시오.

한 예로, 사용자가 보조 프로그램을 켜거나 끌 수 있게 하는 코그너티브 자동차 대시보드 애플리케이션을 작성하려 한다고 가정하십시오. 

1.  가능한 한 많은 실제 고객 질문, 명령 또는 기타 입력을 수집하십시오. 실제 사용자의 입력을 사용하면 전문가가 가능한 표현 목록을 작성하게 하는 것보다 예상 입력에 대해 더 쉽게 설명할 수 있습니다. 고객은 여러 방법으로 동일한 종류의 요청을 표현할 수 있습니다. 예를 들어, 다음 예제 표현은 모두 끄기 요청을 나타냅니다.

    - `Headlights off`
    - `Turn the radio off`
    - `Stop the air conditioner`
1.  예제 목록이 있으면 애플리케이션에서 지원할 기능에 따라 이러한 예제를 카테고리로 정렬하십시오. 예제가 애플리케이션이 새 입력에서 해당 인텐트를 식별하는 데 도움이 되는 반면 이 카테고리는 정의할 인텐트를 나타냅니다.

    인텐트를 너무 비슷하게 작성하지 마십시오. 유사한 인텐트는 {{site.data.keyword.conversationshort}} 서비스에서 구분하기 어려울 수 있습니다. 의미가 비슷한 인텐트가 여러 개 있으면, 이를 단일 인텐트로 결합할지 고려한 다음 엔티티를 사용하여 해당 인텐트에 대해 여러 가능한 응답을 제공하십시오.
    {: tip}

    위의 예제가 모두 동일한 인텐트(끄기)를 나타내므로 이 카테고리 `#turn_off`를 호출할 수 있습니다.
    고객 입력은 예제와 정확하게 일치하지 않습니다. 인텐트는 자연어 처리를 사용하여 인식됩니다.
    {: tip}
1.  그런 다음 엔티티를 사용하여 사용자가 끄려는 대상을 나타냅니다. 이를 수행하기 위해 `@accessory` 엔티티를 작성하고 다음 가능한 값을 제공할 수 있습니다.

    - `headlights`
    - `radio`
    - `air conditioner`

    또한 값마다 동의어를 지정할 수 있습니다. 예를 들어, `AC` 및 `cooling`을 `air conditioner`의 동의어로 지정할 수 있습니다. 세 개의 문자열 모두 동일한 값으로 처리됩니다. 사용자가 동일한 값을 참조하는 여러 방법을 나열하면 애플리케이션의 정확도를 향상시킬 수 있습니다.
1.  사용자 입력이 수신되면 대화가 인텐트와 엔티티 모두 인식합니다. 그러면 대화 상자 플로우가 이 인텐트와 엔티티를 사용하여 최선의 응답을 제공할 수 있습니다. 애플리케이션이 인텐트에 응답하는 방법을 변경한다는 점에서 중요한 내용에 대한 엔티티만 작성해야 합니다.
    서비스는 정의하는 엔티티 외에 이미 정의되어 있고 사용할 수 있는 시스템 엔티티 세트를 제공합니다. 자세한 정보는 [시스템 엔티티 사용](entities.html#enable_system_entities)을 참조하십시오.
    {: tip}
1.  계속해서 필요에 따라 인텐트, 엔티티 및 예제를 세분화하십시오. 인텐트와 엔티티 세트를 완료된 프로시저로 간주하지 마십시오. [대화 상자를 빌드](dialog-build.html)할 때, 추가해야 하는 인텐트와 엔티티를 식별할 수 있습니다. 또한 계속해서 새 고객의 입력을 수집하고 이를 사용하여 새 예제를 추가할 수 있습니다. 이 반복 프로세스는 인텐트와 엔티티를 정확하게 인식하는 애플리케이션의 기능을 향상시킵니다.