* create state
* changing state | using state

###### To make a statefullWidget, we need to create two classes, one for the state and other for the widget

in the given below code, DiceRoller class is used to create state and "_DiceRollerState_" is used to make the widget

To create a state, use "createState()"
To re-render on state change, use the function "setState"
```
import 'dart:math';
import 'package:flutter/material.dart';

var randomizer = Random();

class DiceRoller extends StatefulWidget {
  const DiceRoller({super.key});

  @override
  State<DiceRoller> createState() {
    return _DiceRollerState();
  }
}

class _DiceRollerState extends State<DiceRoller> {
  var activeDiceImage = "assets/images/dice-2.png";
  void rollDice() {
    var diceRoll = randomizer.nextInt(6) + 1;
    setState(() {
      activeDiceImage = "assets/images/dice-$diceRoll.png";
    });
  }

  @override
  Widget build(context) {
    return Column(
      mainAxisSize: MainAxisSize.min,
      children: [
        Image.asset(
          activeDiceImage,
          width: 200,
        ),
        const SizedBox(
          height: 16,
        ),
        TextButton(
          onPressed: rollDice,
          style: TextButton.styleFrom(
            // padding: const EdgeInsets.all(16),
            foregroundColor: Colors.white,
            textStyle: const TextStyle(fontSize: 32),
          ),
          child: const Text("Roll the dice!"),
        ),
      ],
    );
  }
}
```