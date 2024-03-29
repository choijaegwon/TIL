# Parse

## 예시 코드
~~~
import SwiftUI

protocol DataParserProtocol {
    func parse<T: Decodable>(data: Data) throws -> T
}

class DataParser: DataParserProtocol {
    private var jsonDecoder: JSONDecoder

    init(jsonDecoder: JSONDecoder = JSONDecoder()) {
        self.jsonDecoder = jsonDecoder
        self.jsonDecoder.keyDecodingStrategy = .convertFromSnakeCase
        // print("DataParser init")
    }

    deinit {
        // print("DataParser deinit")
    }

    func parse<T: Decodable>(data: Data) throws -> T {
        if T.self == String.self {
            return String(data: data, encoding: .utf8) as! T
        }
        return try self.jsonDecoder.decode(T.self, from: data)
    }
}
~~~

사용법

~~~
private var parser: DataParserProtocol {
    return DataParser()
}
~~~

~~~
let decoded: JoinLiveResponse = try self.parser.parse(data: jsonData)
~~~