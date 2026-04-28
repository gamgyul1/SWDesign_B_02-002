```mermaid
graph LR
    %% 액터 정의
    Customer((고객))
    Admin((관리자))

    %% 시스템 경계
    subgraph 리조트 객실예약 시스템
        %% 고객 관련 유스케이스
        UC_고객등록([고객등록])
        UC_고객조회([고객조회])
        UC_고객인증([고객인증])

        %% 객실 관련 유스케이스
        UC_객실등록([객실등록])
        UC_객실조회([객실조회])
        UC_객실가격조회([객실가격조회])

        %% 예약 관련 유스케이스
        UC_예약([예약])
        UC_취소([취소])
        UC_예약조회([예약조회])
    end

    %% 액터와 일반 유스케이스 연관 관계 (Association)
    Customer --- UC_고객등록
    Customer --- UC_고객조회
    Customer --- UC_고객인증
    Customer --- UC_객실조회
    Customer --- UC_객실가격조회
    Customer --- UC_예약
    Customer --- UC_취소
    Customer --- UC_예약조회

    Admin --- UC_객실등록

    %% 포함(Include) 관계 정의 (요구사항 반영)
    %% "예약 시 반드시 고객인증과 객실조회를 해야하며"
    UC_예약 -. "<< include >>" .-> UC_고객인증
    UC_예약 -. "<< include >>" .-> UC_객실조회

    %% "취소 시 반드시 예약조회와 고객조회를 해야한다"
    UC_취소 -. "<< include >>" .-> UC_예약조회
    UC_취소 -. "<< include >>" .-> UC_고객조회