```mermaid
classDiagram
	class 고객정보 {
		-id: String
		-암호: String
		-성명: String
		+고객등록(id: String, 암호: String, 성명: String) boolean
		+고객조회(id: String) boolean
		+고객인증(id: String) boolean
	}
	class 객실정보 {
		-객실id: String
		-평수: int
		-객실가격: double
		+객실등록(객실id: String, 평수 int, 객실가격 double) boolean
		+객실조회(객실id: String) boolean
		+객실가격조회(객실id: String) double
	}
	class 예약정보 {
		-예약id: String
		-id: String
		-객실id: String
		-숙박일자: int
		-숙박기간: int
		-총비용: double
		+예약(id: String, 객실id: String, 숙박일자: int, 숙박기간: int) double
		+취소(예약id: String, id: String) boolean
	}
	class Reservation {
	}
	객실정보 "1" <-- "0..*" 예약정보
	고객정보 "1" <-- "1" 예약정보
	예약정보 <.. Reservation