# digiworld (디지월드)
API support for testing new strategies
(전략을 테스트하기 위한 API)

##### URL

https://www.dongkye.tech/digiworld?api_key={{ your api key }}

##### POST

| Parameters                 | Datetype           | Values (허용 값) | Description (설명) |
| -------------------------- |:------------------:| ---------------:|:------------|
| request_datetime           | datetime           |                 | Datetime when order was requested (주문이 입력되었을 때의 일시) |
| real_datetime              | datetime           |                 | Datetime when order was completed (주문이 실제로 결제되었을 때의 일시) |
| strategy_name              | string             |                 | Your registered strategy name (등록되어 있는 가칭-펀드명) |
| ticker                     | string             |                 | Ticker of the traded product (거래된 상품의 코드명) |
| market                     | string             | Ex. Binance     | Platform in which the product was traded (상품이 거래된 플렛폼) |
| action                     | int                | 1: buy, 2: sell | Buy / sell (매수 / 매도) |
| total_price                | float              |                 | Total price paid or received that includes the fees (수수료를 포함한 총 금액) |
| bare_price                 | float              |                 | The spot price on which the trade was accomplished (거래된 스팟가격) |
| order_size                 | float              |                 | The volume traded (거래된 수량) |
| holding_volume             | float              |                 | Holding volume of the traded product after this trade was accomplished (해당 거래 직후에 보유하고 있는 수량) |
| misc (optional)            | string             |                 | Notes to add for this transaction (선택사항 - 해당 거래에 대해 기록하고 싶은 내용) |

##### GET

| Required Parameters - Name (중요) | Values (허용 값)                                  |
| -------------------------- |:--------------------------------------------------------|
| strategy_name              | Your registered strategy name (등록되어 있는 가칭-펀드명) |
| api_key                    | Your api key                                            |

##### RESULT

{ result: result_code }

| result_code | Description (설명)                           |
|-------------|----------------------------------------------|
|200          | Successful (성공적)                           |
|100          | Invalid API Key (API Key가 거부됨)            |
|101          | Authentication Failed (인증 실패)             |
|201          | Connection Error (연결 불안정)                |
|300          | Missing Parameters (변수 부족)                |
|301          | strategy_name is invalid or not string       |
|302          | ticker is invalid or not string              |
|303          | market is invalid or not string              |
|304          | misc is not string                           |
|305          | action is not a valid integer                |
|306          | holding_volume is invalid or not float       |
|307          | total_price is invalid or not float          |
|308          | bare_price is invalid or not float           |
|309          | order_size is invalid or not float           |
|310          | request_datetime is invalid or not datetime  |
|311          | real_datetime is invalid or not datetime     |
