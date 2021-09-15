import 'dart:html';
import 'dart:io';
import 'package:flutter/material.dart';
import 'package:flutter/cupertino.dart';

void main(){
  runApp(Calculator());

}

class Calculator extends StatelessWidget{
  @override
  Widget build(BuildContext context){
    return MaterialApp(
      home: HomeView(),
      debugShowCheckedModeBanner: false,
      theme:ThemeData(primarySwatch: Colors.blue ),
    );
  }
}

class HomeView extends StatefulWidget{
  HomeView ({Key? key}) : super (key: key);
  @override
_HomeViewState createState () => _HomeViewState ();
}
class _HomeViewState extends State<HomeView>{
List <String> keypads =
  ["AC",
    "+/-",
   "%",
   "/",
   "7",
   "8",
   "9",
    "*",
   "4",
    "5",
    "6",
    "-",
    "1",
    "2",
    "3",
    "+",
    "0",
    ".",
    "=",
    ];
  bool isOperator({required String label}){
    return
   label =="/" ||
    label =="*"||
    label =="+"||
    label =="="||
    label =="-";
  }
   String answer ="";
   String input ="";

   Widget build(BuildContext context) {
    return Scaffold(backgroundColor: Colors.black,
    appBar:AppBar(
      backgroundColor: Colors.transparent,
      title: Text ('WomanRising'),
      centerTitle: true,
      actions: [
      Icon(
        Icons.history,
        color: Colors.white,
      ),
        SizedBox(width: 20),

      ],
    ) ,
      drawer:Drawer(),
      body: Padding (
        padding: const EdgeInsets.symmetric(horizontal: 30,
            vertical:20),
     child: Column(
        crossAxisAlignment: CrossAxisAlignment.end,
        children: [
          Text(
            answer,
         style: TextStyle(
           color: Colors.black12,
           fontSize: 42,
         ),
          ),
          SizedBox(height: 20,),
          Text(
           input,style:TextStyle(
           color:Colors.grey,
            fontSize:20,),
            Expanded(
             child:GridView.builder(
               itemCount:keypads.length,
               gridDelegate:SilverGridDelegateWithFixedCrossAxisCount(
                 crossAxisCount:4,
                 crossAxisSpacing:15,
                 mainAxisSpacing:15,
               ),
               itemBuilder:(context,index) {
                 final String keypad= keypads[index];
                 return TextButton(
                  style:TestButton. styleFrom (
                    backgroundColor: isOperator(label: keypad)
                        ?Colors.amber
                        :Colors.blueGrey
                        shape: isOperator (label:keypad)
                      ?CircleBorder()
                      :RoundedRectanguleBorder(
                    borderRadius:BorderRadius.circular(0),
                  ),
                  ),
                 onPressed:(){
                    handleKeyOnPressed(keypad:keypad);
                 },
                 child:Text(
                 keypad,
                 style:TextStyle(
                 color: Colors.white,
                 ),
                 ),
                 );
               }
             ),
            ),
          )

        ],
      )

      )
    );
        ;


   }
    String calcIntput(){
     print("inputValue:$input");
     final result = buildParser().parser(input);
     if(result.isSuccess){
       print(result.value);
       setState((){
        answer=result.value.toString();

       }else(setState()){answer=" Error";});


       )
     }
     print("Error$result");
     return"Error Hey Illy";
    }


}
void handleKeyOnProssed({requried string keypad}){
 setState((){
   if(keypad== "AC") {
     input ="";
     answer="";
   } else if (keypad =="<" && input.isNotEmpty)
     input=input.substring(0,input.lenght-1);
     else if (keypad =="0"){
      if(input.isEmpty)
        input = keypad;
      else if(input.lenght== 1 && input ==keypad)
        return;
      else if

   }
      }

 }



 )



}