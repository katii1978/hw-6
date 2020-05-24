import 'package:flutter/material.dart';

void main() {
  runApp(
    mainLayout(),
  );
}

Widget menuBar() {
  return Row(
    mainAxisAlignment: MainAxisAlignment.spaceBetween,
    children: [
      icon('menu', 24.0),
      icon('search', 24.0),
    ],
  );
}

Widget icon(name, size, {padding = 8.0}) {
  return Container(
    width: size,
    height: size,
    margin: EdgeInsets.all(padding),
    child: Image.network('https://storage.yandexcloud.net/goitgirls/$name.png'),
  );
}

Widget productBanners() {
  return ListView(
    scrollDirection: Axis.horizontal,
    children: [
      product('chair3d', Colors.teal[100], "Origami\nChair"),
      product('chair3d2', Colors.purple[100], "Adirondak\nChair"),
      product('chair3d2', Colors.orangeAccent, "Origami\nChair"),
      product('chair3d', Colors.greenAccent, "Adirondak\nChair"),
    ],
  );
}

Widget product(
  String iconName,
  Color backgroundColor,
  String title,
) {
  return Material(
    child: Container(
      width: 188,
      height: 188,
      margin: EdgeInsets.only(left: 24),
      decoration: BoxDecoration(
        borderRadius: BorderRadius.all(Radius.circular(32)),
        color: backgroundColor,
      ),
      child: Stack(
        children: [
          Positioned(
            left: 20,
            top: 20,
            child: Text(
              title,
              style: TextStyle(
                color: Colors.white,
                fontSize: 24,
                decoration: null,
                decorationStyle: null,
              ),
            ),
          ),
          Positioned(
            bottom: 0,
            right: 0,
            child: icon(iconName, 140.0),
          )
        ],
      ),
    ),
  );
}

Widget mainLayout() {
  return MaterialApp(
    theme: ThemeData(fontFamily: 'Avenir'),
    home: Container(
      color: Colors.white,
      child: Column(children: [
        Container(
          height: 80,
          padding: EdgeInsets.symmetric(horizontal: 16),
          child: menuBar(),
        ),
        Container(
          height: 188,
          margin: EdgeInsets.symmetric(vertical: 24),
          child: productBanners(),
        ),
        Container(
          height: 44,
          alignment: Alignment.topLeft,
          padding: EdgeInsets.only(left: 16),
          child: catalogHeader(),
        ),
        Expanded(
          child: catalogGrid(),
        )
      ]),
    ),
  );
}

Widget catalogHeader() {
  return Material(
    child: Text(
      'Browse Furniture',
      style: TextStyle(color: Colors.black, fontSize: 32.0),
    ),
  );
}

Widget catalogGrid() {
  return SingleChildScrollView(
    child: Container(
      padding: EdgeInsets.symmetric(horizontal: 16),
      child: Column(
        children: <Widget>[
          catalogFirstRow(),
          catalogSecondRow(),
          catalogThirdRow(),
        ],
      ),
    ),
  );
}

Widget catalogFirstRow() {
  return Row(
    mainAxisAlignment: MainAxisAlignment.spaceBetween,
    children: <Widget>[
      category('chairs', 'Chairs'),
      category('sofa', 'Sofa'),
      category('racks', 'Racks'),
    ],
  );
}

Widget catalogSecondRow() {
  return Row(
    mainAxisAlignment: MainAxisAlignment.spaceBetween,
    children: <Widget>[
      category('carpet', 'Carpet'),
      category('chandelier', 'Chandelier'),
      category('bed', 'Bed'),
    ],
  );
}

Widget catalogThirdRow() {
  return Row(
    mainAxisAlignment: MainAxisAlignment.spaceBetween,
    children: <Widget>[
      category('work-station', 'Workstation'),
      category('book-shelf', 'Book Shelf'),
      category('bean-bag', 'Bean Bag'),
    ],
  );
}

Widget category(String iconName, String name) {
  return Material(
    child: Column(
      children: <Widget>[
        icon(iconName, 60.0),
        Text(
          name,
          style: TextStyle(
            color: Colors.black,
            fontSize: 12,
          ),
        ),
      ],
    ),
  );
}
