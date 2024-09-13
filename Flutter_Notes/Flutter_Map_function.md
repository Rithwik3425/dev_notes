![[Pasted image 20240325162644.png]]

```
Column(
            children: currentQuestion.answers.map((answer) {
              return AnswerButton(
                answerText: answer,
                onTap: nextQuestion,
              );
            }).toList(),
          ),
```

or

```
...currentQuestion.answers.map(
            (answer) {
              return AnswerButton(
                answerText: answer,
                onTap: nextQuestion,
              );
            },
          ),
```