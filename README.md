import 'dart:math';
import 'package:flutter/material.dart';

class DiceRoller extends StatefulWidget{
  const DiceRoller({super.key});
  State<DiceRoller> createState(){
    return _DiceRollerState();
  }
}
class _DiceRollerState extends State<DiceRoller>{
  var currentDiceRoll =2;
  void rollDice(){
    setState(() {          //state update karni hu tu
      currentDiceRoll=Random().nextInt(6)+1;
    });
  }
  Widget build(context){
    return Center(
      child: Column(
        mainAxisSize: MainAxisSize.min,
        children: [
          Image.asset('assets/images/dice-$currentDiceRoll.png',width: 200,),
          const SizedBox(height: 20),
          TextButton(
              onPressed: rollDice,
              style: TextButton.styleFrom(
              foregroundColor: Colors.white,
              textStyle:const TextStyle(
                fontSize: 28,
              ),
              ),
              child: const Text('Roll Dice'),
          ),
          TextFormField(
            validator:(value){
              if (value!.isEmpty){
                return "Please Enter you name";
              }
              return null;
            },
          )
        ],
      ),
    );
  }
}
