# ChipView

## 디자인
<img width="248" alt="Untitled" src="https://github.com/choijaegwon/choijaegwon.github.io/assets/68246962/3e092b46-7601-492c-98d7-8384dcd981fd">

## 구현코드
~~~
import 'package:flutter/material.dart';

class CustomChip extends StatelessWidget {
  String imageStr;
  String title;
  String detail;
  Color? color;

  CustomChip({
    required this.imageStr,
    required this.title,
    required this.detail,
    this.color,
  });

  @override
  Widget build(BuildContext context) {
    return Container(
      padding: EdgeInsets.only(top: 12, bottom: 12, left: 16, right: 16),
      decoration: BoxDecoration(
        color: Colors.black,
        borderRadius: BorderRadius.circular(26),
      ),
      child: Row(
        children: [
          Image.asset(
            imageStr,
            width: 24,
            height: 24,
          ),
          Container(
            margin: EdgeInsets.only(left: 4),
            child: Text(
              title,
              style: TextStyle(
                color: Colors.white,
              ),
            ),
          ),
          Container(
            margin: EdgeInsets.only(left: 8),
            child: Text(
              detail,
              style: TextStyle(
                  color: color,
                  fontWeight: FontWeight.bold),
            ),
          ),
        ],
      ),
    );
  }
}
~~~