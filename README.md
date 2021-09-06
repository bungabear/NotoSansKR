# NotoSansKR

폰트 출처 : https://fonts.google.com/specimen/Noto+Sans+KR#standard-styles

Flutter Dynamic Font용  


```dart
import 'dart:ui';

import 'package:dynamic_fonts/dynamic_fonts.dart';
import 'package:flutter/material.dart';

class NanumSquareFont extends DynamicFontsFile {

  final DynamicFontsVariant variant;
  final NotoSansKRFontType type;
  static final String fontFamily = 'NotoSansKR';

  NanumSquareFont(this.variant)
      :
        type = NanumSquareFontTypeEx.getType(variant),
        super(NanumSquareFontTypeEx.getType(variant).hash, NanumSquareFontTypeEx.getType(variant).size);

  /// ThemeData.textTheme 에 적용
  static TextTheme getTextTheme({TextTheme textTheme}){
    return DynamicFonts.getTextTheme(
      NanumSquareFont.fontFamily,
      textTheme,
    );
  }

  /// main super.initState() 위에 선언
  static register(){
    print('$fontFamily register start');
    DynamicFonts.register(
      fontFamily,
      FontWeight.values.map((FontWeight fontWeight){
        return NanumSquareFont(
          DynamicFontsVariant(
            fontWeight: fontWeight,
            fontStyle: FontStyle.normal,
          ),
        );
      }).toList()
          .fold<Map<DynamicFontsVariant, DynamicFontsFile>>(
        {},
            (acc, file) => acc..[file.variant] = file,
      ),
    );
    print('$fontFamily registerd');
  }

  @override
  String get url {
    String url = 'https://github.com/bungabear/NotoSansKR/blob/main/NotoSansKR-${type.fileFix}.otf?raw=true';
    print('$fontFamily call $url');
    return url;
  }
}

enum NotoSansKRFontType {
  Thin, Light, Regular, Medium, Bold, Black
}

extension NanumSquareFontTypeEx on NotoSansKRFontType{

  // 폰트 타입 분기
  static NotoSansKRFontType getType(DynamicFontsVariant variant) {
    NotoSansKRFontType type = NotoSansKRFontType.Regular;
    switch(variant.fontWeight){
      case FontWeight.w100:
        type = NotoSansKRFontType.Thin;
        break;
      case FontWeight.w200:
        type = NotoSansKRFontType.Thin;
        break;
      case FontWeight.w300:
        type = NotoSansKRFontType.Light;
        break;
      case FontWeight.w400:
        type = NotoSansKRFontType.Regular;
        break;
      case FontWeight.w500:
        type = NotoSansKRFontType.Medium;
        break;
      case FontWeight.w600:
        type = NotoSansKRFontType.Medium;
        break;
      case FontWeight.w700:
        type = NotoSansKRFontType.Bold;
        break;
      case FontWeight.w800:
        type = NotoSansKRFontType.Black;
        break;
      case FontWeight.w900:
        type = NotoSansKRFontType.Black;
        break;
      default:
        print('font type error ${variant.fontWeight}');
    }
    return type;
  }

  String getFileFix(DynamicFontsVariant variant){
    return getType(variant).fileFix;
  }

  /// 파일 해쉬 선언
  String get hash{
    switch(this){
      case NotoSansKRFontType.Thin:
        return '7654babf95b0e7cbe45c2bb15d432dc20524a42fbd959eb0776b00779e6325fc';
      case NotoSansKRFontType.Regular:
        return '2f62e282b5ff3694c09af182d0dfc29d46ce6b85303c0da74f159c098e75991b';
      case NotoSansKRFontType.Bold:
        return '7deb7d6a71b3230a8a505d2cfaa484baacb953c79ca5b28dcc78db8077774c0d';
      case NotoSansKRFontType.Black:
        return '88ea5f1d54b29c49d36d8465b09181a1bdd8983877c4d781f0cd025b739cd5be';
      case NotoSansKRFontType.Light:
        return '980ae40205193422dc61b48bcc7ebcfd16b3958f93653f547d83dd44c8b06cdf';
      case NotoSansKRFontType.Medium:
        return '857cd8ad732da87ca1ea50bae3029fa370b02f5553ad9acd1c6674ca13fe05c5';
    }
  }

  /// 파일크기 선언
  int get size{
    switch(this){
      case NotoSansKRFontType.Thin:
        return 4383664;
      case NotoSansKRFontType.Regular:
        return 4744644;
      case NotoSansKRFontType.Bold:
        return 4909620;
      case NotoSansKRFontType.Black:
        return 5068176;
      case NotoSansKRFontType.Light:
        return 4713884;
      case NotoSansKRFontType.Medium:
        return 4768724;
    }
  }

  /// 파일명 선언
  String get fileFix{
    switch(this){
      case NotoSansKRFontType.Thin:
        return 'Thin';
      case NotoSansKRFontType.Regular:
        return 'Regular';
      case NotoSansKRFontType.Bold:
        return 'Bold';
      case NotoSansKRFontType.Black:
        return 'Black';
      case NotoSansKRFontType.Light:
        return 'Light';
      case NotoSansKRFontType.Medium:
        return 'Medium';
    }
  }
}
```
