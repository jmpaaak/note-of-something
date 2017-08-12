# note-of-something
Note of somethings (using Markdown)

## Logstash
#### 구현 과정
* NodeJS 모듈 logstash-client 를 사용하여 로컬 PC 의 Logstash 포트에 json 입력 전송
    - TCP 를 이용한 네트워크 입력 사용
    - 모듈 예제 코드 링크 - https://www.npmjs.com/package/logstash-client#clientsend
* Logstash 에서는 받아온 입력에 json 필드를 추가하거나 변경하는 작업을 Filter 에서 수행
    - Json 에서 **처리할 필드만 나열하여 문자열로 만들어 Kafka 브로커로 전송** 하므로 현재 Filter 가 요구되는 컬럼이 없음
* Logstash 의 출력으로 Kafka broker 주소 및 plain text 형태를 사용
    - 설정 옵션으로 `topic_id` 를 넘겨주어야함
    - ex.
    ```
    output {
      kafka {
        codec => plain {
           format => "%{message}"
        }
        topic_id => "mytopic"
      }
    }
    ```

#### 구현 결과
* Kafka 서버 구성 전이므로 Logstash 의 Output 을 로컬 표준 출력으로 하여 확인 완료
```
(Logstash 출력 화면)
```
