```
import 'pacakage:flutter/material.dart';

void main(){
	runnApp( MaterialApp(
			home: Scaffold(
				body: Container(
					decoration: const BoxDecoration(
						gradient: LinearGradient(
							colors: [
								color.fromARGB(225,0,0,165),
								color.fromARGB(225,0,0,84),
							],
							begin: Alignment.topLeft,
							end: Alignment.bottomRight,
						), //LinearGradient
					), //BoxDecoration
					child: const Center(
						child: Text(
							'Hello World!',
							style: TextStyle(
								fontSize: 30, 
								color: Colors.white
							), //Text
						), 
					),//Center
				),//Container
			),//Scaffold
		),
	);//Material App
}
```