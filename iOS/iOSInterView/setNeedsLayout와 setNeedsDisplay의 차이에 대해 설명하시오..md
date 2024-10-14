# setNeedsLayout와 setNeedsDisplay의 차이에 대해 설명하시오.

- setNeedsLayout()메소드와 setNeedsDisplay() 메소드 모두 호출 즉시 실행되지 않고 다음 update cycle에 변경사항이 적용됩니다.
- setNeedsLayout은 layoutSubview메소드를 setNeedsDisplay는 draw메소드를 시스템이 호출하게끔 유도한다.
- setNeedsLayout() 메소드는 모든 핸들러가 종료되고 권한이 main run loop로 돌아오는 시점에 view의 position이나 layout에 관한 변화를 적용시키고 setNeedsDisplay() 메소드는 다음 드로잉 사이클이 오면 그 때 쌓여있는 그려야할 컨텐츠들을 동시에 적용시킵니다.