---
title: 'Návod: ladění v době návrhu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], design-time
- breakpoints, design-time debugging
- Immediate window, design-time debugging
- design-time debugging
ms.assetid: 35bfdd2c-6f60-4be1-ba9d-55fce70ee4d8
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 54466cc3561c194199bbad2b35cd00433da2b0f3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149420"
---
# <a name="walkthrough-debugging-at-design-time"></a>Návod: Ladění v době návrhu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

K provedení funkce nebo podrutiny v době, kdy vaše aplikace neběží, můžete použít okno Visual Studio **Immediate** . Pokud funkce nebo podprogram obsahuje zarážku, Visual Studio pozastaví provádění v příslušném bodě. Pak můžete použít okna ladicího programu k prohlédnutí stavu programu. Tato funkce se nazývá ladění v době návrhu.  
  
 Následující postup ukazuje, jak můžete tuto funkci používat.  
  
### <a name="to-hit-breakpoints-from-the-immediate-window"></a>Volání zarážek z příkazového podokna  
  
1. Do Visual Basic konzolové aplikace vložte následující kód:  
  
    ```  
    Module Module1  
  
        Sub Main()  
            MySub()  
        End Sub  
  
        Function MyFunction() As Decimal  
            Static i As Integer  
            i = i + 1  
            Dim s As String  
  
            s = "Add Breakpoint here"  
            Return 4  
        End Function  
  
        Sub MySub()  
            MyFunction()  
        End Sub  
    End Module  
    ```  
  
2. Nastavte zarážku na řádku, který čte, `s="Add BreakPoint Here"` .  
  
3. Do příkazového **podokna zadejte** následující: `?MyFunction<enter>`  
  
4. Ověřte, zda byla zarážka zavolána a zda je zásobník volání přesný.  
  
5. V nabídce **ladit** klikněte na tlačítko **pokračovat**a ověřte, zda jste stále v režimu návrhu.  
  
6. Do příkazového **podokna zadejte** následující: `?MyFunction<enter>`  
  
7. Do příkazového **podokna zadejte** následující: `?MySub<enter>`  
  
8. Ověřte, zda jste narazili na zarážku, a zkontrolujte hodnotu statické proměnné `i` v okně **místní** hodnoty. Hodnota by měla mít hodnotu 3.  
  
9. Ověřte, zda je zásobník volání přesný.  
  
10. V nabídce **ladit** klikněte na tlačítko **pokračovat**a ověřte, zda jste stále v režimu návrhu.  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečení ladicího programu](../debugger/debugger-security.md)   
 [Základy ladicího programu](../debugger/debugger-basics.md)
