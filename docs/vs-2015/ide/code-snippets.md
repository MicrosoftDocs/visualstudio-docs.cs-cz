---
title: Fragmenty kódu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.ExpansionManagerImport
- vs.codesnippetmanager
helpviewer_keywords:
- code snippets, replacement parameters
- code snippets, surround with
- replacement parameters
- code snippets, expansion
- surround with
- code snippets
ms.assetid: 85976ad9-4c9a-4e7b-896e-66ec6f955199
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 317471f73c9e7507768b9b600ce995a35b000c23
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49242166"
---
# <a name="code-snippets"></a>Fragmenty kódu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Fragmenty kódu jsou malé bloky opakovaně použitelný kód, který může být vložen do souboru kódu pomocí příkazu kontextové nabídky nebo kombinace klávesových zkratek. Obvykle obsahují kód běžně používaných bloků, například try-finally nebo if-else bloky, ale slouží k vložení celého třídy nebo metody.  
  
## <a name="expansion-snippets-and-surround-with-snippets"></a>Rozšíření fragmentů a příkazu Obklopit s fragmenty kódu  
 V sadě Visual Studio existují dva druhy fragment kódu: fragmenty kódu rozšíření, které jsou přidány zadaný kurzoru a mohou nahradit místní fragment kódu, a příkazu Obklopit s fragmenty kódu (C# a C++ pouze), které se přidají okolo vybraného bloku kódu.  
  
 Příklad vložení fragmentu kódu: v jazyce C# tryf místní slouží k vložení bloku try-finally:  
  
```  
try  
{  
  
}  
finally  
{  
  
}  
  
```  
  
 Tento fragment kódu lze vložit kliknutím **Vložit fragment** v místní nabídce okna kódu, pak **Visual C#**, zadejte `tryf`, pak kartu, nebo můžete zadat `tryf` a stiskněte klávesu TAB + TAB.  
  
 Příklad obklopit fragmentem: v jazyce C++ zástupce `if` lze použít jako fragment vložení nebo jako obklopit fragmentem. Pokud vyberete řádek kódu (například `return FALSE;`) a potom klikněte na tlačítko **obklopit fragmentem**, pak **Pokud**, fragment kódu je rozbalený kolem řádku:  
  
```  
if (true)  
{  
    return FALSE;  
}  
  
```  
  
## <a name="snippet-replacement-parameters"></a>Fragment kódu nahrazující parametry  
 Fragmenty kódu může obsahovat náhradní parametry, které jsou zástupné symboly, které je třeba nahradit podle přesný kód, který píšete. V předchozím příkladu `true` je parametr nahrazení, který by nahraďte vhodné podmínky. Nahrazení provedené se opakuje pro každou instanci stejné nahrazení parametrů v tomto fragmentu kódu.  
  
 Například v jazyce Visual Basic je fragment kódu, který se vkládá vlastnost. Klikněte na tlačítko **Vložit fragment** v místní nabídce okna kódu, pak **vzorů v kódu**, pak **vlastnosti, procedury, události**, nadefinujte typ vlastnosti. Následující kód je vložen:  
  
```  
Private newPropertyValue As String  
Public Property NewProperty() As String  
    Get  
        Return newPropertyValue  
    End Get  
    Set(ByVal value As String)  
        newPropertyValue = value  
    End Set  
End Property  
  
```  
  
 Pokud změníte `newPropertyValue` k `m_property`, pak každá instance `newPropertyValue` se změnilo. Pokud změníte `String` k `Int` v deklaraci vlastnosti, pak hodnota metody set se také změní na `Int`.  
  
## <a name="code-snippet-manager"></a>Správce fragmentů kódů  
 Všechny fragmenty kódu, které jsou aktuálně nainstalovány a jejich umístění můžete zobrazit na disku, kliknutím **nástroje/Správce fragmentů kódů**. Fragmenty kódu se zobrazují v jazyce.  
  
 Můžete přidávat a odebírat adresářů fragment kódu se pomocí **přidat** a **odebrat** tlačítka v **Správce fragmentů kódů** dialogového okna. Chcete-li přidat jednotlivé fragmenty kódu, použijte **Import** tlačítko.  
  
## <a name="see-also"></a>Viz také  
 [Návod: Vytvoření fragmentu kódu](../ide/walkthrough-creating-a-code-snippet.md)   
 [Postupy: distribuce fragmentů kódu](../ide/how-to-distribute-code-snippets.md)   
 [Osvědčené postupy pro používání fragmentů kódu](../ide/best-practices-for-using-code-snippets.md)   
 [Řešení potíží s fragmenty kódu](../ide/troubleshooting-snippets.md)   
 [Fragmenty kódu jazyka Visual C#](../ide/visual-csharp-code-snippets.md)   
 [Fragmenty kódu Visual C++](../ide/visual-cpp-code-snippets.md)   
 [Fragmenty kódu – odkaz schématu](../ide/code-snippets-schema-reference.md)



