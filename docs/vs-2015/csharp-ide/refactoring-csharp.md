---
title: Refaktoring (C#) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.csharp.refactoring.preview
- vs.csharp.refactoring.issues
- vs.csharp.refactoring.buildwarning
- VS.PreviewChanges
dev_langs:
- CSharp
helpviewer_keywords:
- refactoring [C#]
ms.assetid: a39e656a-f81f-4c87-b484-a23168ff1dfc
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: b4f74017a067d4681eb14ba4eb826df504497430
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49262311"
---
# <a name="refactoring-c"></a>Refaktoring (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Refaktoring je proces vylepšení kódu po byl zapsán tak, že změníte interní strukturu kódu beze změny externí chování kódu.  
  
 Visual C# umožňuje refaktoringu pomocí následujících příkazů na **refaktoringu** nabídky:  
  
-   [Refaktoring pro extrahování metody (C#)](../csharp-ide/extract-method-refactoring-csharp.md)  
  
-   [Refaktoring pro přejmenování (C#)](../csharp-ide/rename-refactoring-csharp.md)  
  
-   [Refaktoring pro zapouzdření polí (C#)](../csharp-ide/encapsulate-field-refactoring-csharp.md)  
  
-   [Refaktoring pro extrahování rozhraní (C#)](../csharp-ide/extract-interface-refactoring-csharp.md)  
  
-   [Refaktoring pro odebrání parametrů (C#)](../csharp-ide/remove-parameters-refactoring-csharp.md)  
  
-   [Refaktoring pro přeskupení parametrů (C#)](../csharp-ide/reorder-parameters-refactoring-csharp.md)  
  
## <a name="multi-project-refactoring"></a>Refaktoring vícenásobného projektu  
 Visual Studio podporuje víceprojektové refaktoring pro projekty, které jsou ve stejném řešení. Všechny operace refaktoringu, které opravit odkazy napříč soubory opravit tyto odkazy ve všech projektech stejný jazyk. Tento postup funguje pro všechny odkazy typu projekt projekt. Například, pokud budete mít konzolovou aplikaci, která odkazuje na knihovnu tříd při přejmenování typ knihovny tříd (pomocí `Rename` operace refaktoringu), jsou aktualizovány také odkazy na typ třídy knihovny v konzolové aplikaci.  
  
## <a name="changes-preview"></a>Změny ve verzi Preview  
 Mnoho operací refaktoringu poskytnout příležitosti ke kontrole všech změn odkazu, které by provádí operaci refaktoringu kódu, před potvrzením změn. Pro tyto operace, refaktoring **náhled změn odkazů** možnost se zobrazí v dialogovém okně refaktoringu. Po výběru této možnosti a přijímá operaci refaktoringu, **dialogové okno změny ve verzi Preview** se zobrazí. Všimněte si, **náhled změn** dialogové okno obsahuje dvě zobrazení. Zobrazení ve spodní části se zobrazí všechny aktualizace odkaz z důvodu operace refaktoringu kódu. Stisknutím klávesy **zrušit** na **náhled změn** dialogové okno se ukončí operaci refaktoringu a nebudou provedeny žádné změny kódu.  
  
## <a name="refactoring-warnings"></a>Refaktoring upozornění  
 Pokud kompilátor nemá porozumět programu a je možné, že modul refaktoringu nemusí aktualizovat všechny příslušné odkazy, zobrazí se dialogové okno upozornění. Toto dialogové okno upozornění poskytuje také příležitost si můžete zobrazit náhled kódu v **náhled změn** dialogovému oknu před potvrzením změn.  
  
> [!NOTE]
>  Pokud metoda obsahuje chybu syntaxe (což znamená, integrovaného vývojového prostředí s červenou vlnovkou), refaktoringu modul nebude aktualizovat všechny odkazy na prvek v rámci této metody. Následující příklad ukazuje toto chování.  
  
 Ve výchozím nastavení, pokud spustíte operaci refaktoringu bez zobrazení náhledu odkazu změní a zjištění chyby kompilace ve svém programu a potom zobrazí toto dialogové okno upozornění vývojové prostředí.  
  
 Pokud spustíte operaci refaktoringu kódu, který má **náhled změn odkazu** povolená a zjištění chyby kompilace ve svém programu, pak vývojového prostředí se zobrazí následující zpráva upozornění v dolní části **Náhled změn** dialogové okno, namísto zobrazení **refaktoring upozornění** dialogové okno:  
  
 **Váš projekt nebo jeden z jeho závislostí nesestaví aktuálně. Odkazy nemusí aktualizovat.**  
  
 Toto upozornění Refaktoring je dostupný jenom pro operací refaktoringu, které poskytují **náhled změn odkazu** možnost.  
  
## <a name="error-tolerant-refactoring-and-verification-results"></a>Refaktoring chyba proti chybám a výsledky ověření  
 Refaktoring je chyba odolný vůči chybám. Jinými slovy můžete provést refaktoring v projektu, který nelze vytvořit. Ale v těchto případech refaktoringu procesu nemusí být nejednoznačná reference správně aktualizován.  
  
 **Výsledky ověření** dialogové okno můžete upozornění, pokud modul refaktoringu zjistí chyby kompilace nebo zjistí, že operaci refaktoringu neúmyslně způsobí, že kód odkaz pro vytvoření vazby na něco jiného než který byl původně vázán na (obnovení vazby problém).  
  
 Chcete-li výsledky ověření funkcí, na **nástroje** nabídky, klikněte na tlačítko **možnosti**. V **možnosti** dialogového okna rozbalte **textový Editor**a potom rozbalte **jazyka C#**. Klikněte na tlačítko **Upřesnit** a vyberte **ověřte výsledky refaktoring** zaškrtávací políčko.  
  
 **Výsledky ověření** dialogové okno odlišuje rozdíl mezi dvěma druhy problémů obnovení vazby.  
  
### <a name="references-whose-definition-will-no-longer-be-the-renamed-symbol"></a>Odkazy, jejichž definice již nebudou přejmenováno symbol  
 Tento druh mění se vazba problém nastane, pokud odkaz již neodkazuje na symbol byl přejmenován. Zvažte například následující kód:  
  
```csharp  
class Example  
{  
    private int a;  
    public Example(int b)  
    {  
        a = b;  
    }  
}  
```  
  
 Pokud používáte refaktoring přejmenování `a` k `b`, zobrazí se toto dialogové okno. Odkaz na proměnnou přejmenováno `a` nyní sváže parametr, který je předán konstruktoru místo vazby do příslušného pole.  
  
### <a name="references-whose-definition-will-now-become-the-renamed-symbol"></a>Odkazy, jejichž definice se stanou teď přejmenované symbol  
 Tento druh mění se vazba problém nastane, pokud najdete odkaz, který dříve neodkazuje na přejmenováno symbol teď přejmenované symbol. Zvažte například následující kód:  
  
```csharp  
class Example  
{  
    private static void Method(object a) { }  
    private static void OtherMethod(int a) { }  
    static void Main(string[] args)  
    {  
        Method(5);  
    }  
}  
```  
  
 Pokud používáte refaktoring přejmenování `OtherMethod` k `Method`, zobrazí se toto dialogové okno. Odkaz v `Main` nyní odkazuje na přetížené metody, která přijímá `int` místo přetížené metody, která přijímá parametr `object` parametru.  
  
## <a name="see-also"></a>Viz také  
 [Použití vývojového prostředí sady Visual Studio pro jazyk C#](../csharp-ide/using-the-visual-studio-development-environment-for-csharp.md)   
 [Postupy: Obnovení fragmentů kódu refaktoringu jazyka C#](../ide/how-to-restore-csharp-refactoring-snippets.md)