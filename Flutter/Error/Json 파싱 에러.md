# Json 파싱 에러

##  상황
~~~
List<dynamic>
~~~
파싱을 한번 더 해야하는데 이 dynamic에 들어가는 건 라이브러리에서 정해줄 수 없다.(필요한 객체가 서로 다 다르기 때문)
따라서 파싱을 하지 못한다고 에러가 뜬다.

## 핵심 코드
~~~
@JsonSerializable(explicitToJson: true)
~~~

## ExCode
~~~
import 'package:json_annotation/json_annotation.dart';

part 'links.g.dart';

@JsonSerializable(explicitToJson: true)
class Links {
  @JsonKey(name: 'links')
  List<Link> links;

  Links({
    required this.links,
  });

  factory Links.fromJson(Map<String, dynamic> json) => _$LinksFromJson(json);
  Map<String, dynamic> toJson() => _$LinksToJson(this);
}

@JsonSerializable(explicitToJson: true)
class Link {
  @JsonKey(name: "url")
  String? url;
  @JsonKey(name: "label")
  String? label;
  @JsonKey(name: "active")
  bool active;

  Link({
    required this.url,
    required this.label,
    required this.active,
  });

  factory Link.fromJson(Map<String, dynamic> json) => _$LinkFromJson(json);
  Map<String, dynamic> toJson() => _$LinkToJson(this);
}
~~~

# Reference
https://stackoverflow.com/questions/60595703/complex-models-with-json-serializable-listobjects-not-converting-to-map   
