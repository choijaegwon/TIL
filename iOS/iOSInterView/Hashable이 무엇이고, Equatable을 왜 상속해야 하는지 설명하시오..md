# Hashable이 무엇이고, Equatable을 왜 상속해야 하는지 설명하시오.

- 해쉬값은 고유값이어야 하므로 고유값인지 식별해 줄 수 있는 “==”함수가 필요합니다. 이 함수는 Equatable 프로토콜 안에 정의되어 있으니 hashable은 equatable프로토콜을 따라야합니다. 기본 데이터 타입도 ==을 통해 비교가 가능하므로 equatable프로토콜을 따릅니다.
- HashTable에서 hash값을 찾기 위해선 key가 필요하고 이 key는 식별할 수 있도록 unique 해야 합니다.

## Hashable
- 정수 hash 값을 제공하는 타입”으로 정의된 프로토콜

## hash
- 해시 함수에 의해 얻어지는 값으로 해시값, 해시코드, 해시 체크섬으로도 불립니다.

## 해시 함수 
- 임의의 길이의 데이터를 고정된 길이의 데이터로 매핑하는 함수

## hashValue
 - 어떠한 데이터를 Hash 함수에 넣게 되면 반환해주는 값