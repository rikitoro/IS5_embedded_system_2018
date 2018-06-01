# CDECv標準命令の命令サイクル

CDECvでは、命令は1ステップ(1クロック)で行われるのではなく、複数のステップを経て実行されます。
一つの命令を実行するのに必要なすべてのステップは命令サイクル(Instruction Cycle)と呼ばれます。
この命令サイクルは、命令をメモリから取り出しどの命令を実行するのかを確定するまでのフェッチサイクル(Fetch Cycle)と、取り出した命令を実際に実行するまでの実行サイクル(Execute Cycle)とに分けられます。

CDECvの標準命令は図5.1に示す命令サイクルで行われます。
F0からF2はフェッチサイクルで、それ以降は実行サイクルです。
フェッチサイクルで行う処理は命令によらず同じですが、実行サイクルは命令によって行う処理が異なります。
そのため、命令の種類により、フェッチサイクルの最後のステップF2から実行サイクルへは分岐が生じます。


![CDECv標準命令の命令サイクル](./assets/instruction_cycle.png "CDECv標準命令の命令サイクル")

<図5.1> CDECv標準命令の命令サイクル

|     |                     | |
|-----|---------------------|-|
| Fn  | Fetch cyle          | |
| MVn | Move                | MOV |
| P2n | 2-operand operation | ADD, ADC, SUB, SBB, AND, OR, EOR |
| P1n | 1-operand operation | INC, DEC, NOT |
| LDn | Load                | LD |
| STn | Store               | ST |
| JPn | Jump (no condition) | JMP |
| JCn | Conditional Jump    | JS, JZ, JC |
