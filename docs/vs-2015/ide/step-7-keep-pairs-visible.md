---
title: 'Krok 7: Páry ve viditelném stavu | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 42e1d08c-7b2e-4efd-9f47-85d6206afe35
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1b796fa9735337b5cc8f8cb8d955b33bc6a77e76
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49189004"
---
# <a name="step-7-keep-pairs-visible"></a>Krok 7: Uchovejte páry ve viditelném stavu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Hra funguje dobře tak dlouho, dokud hráč vybírá pouze dvojice ikon, které neodpovídají. Ale zvažte, co by mělo nastat, pokud hráč vybere shodnou dvojici. Namísto nastavení zmizení ikon zapnutím časovače (pomocí `Start()` metoda), hra měla resetovat sama tak, aby ho je už neudržují přehled o popisky pomocí `firstClicked` a `secondClicked` referenční proměnné bez resetování barev dvou popisků, které byly vybrány.  
  
### <a name="to-keep-pairs-visible"></a>Zachování dvojic viditelných  
  
1.  Přidejte následující `if` příkazu `label_Click()` metoda obslužné rutiny události poblíž konce kódu těsně nad příkazem, kde spouštíte časovač. Při přidávání do programu si kód pořádně prohlédněte. Zamyslete se nad tím, jak kód funguje.  
  
     [!code-csharp[VbExpressTutorial4Step7#9](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step7/cs/form1.cs#9)]
     [!code-vb[VbExpressTutorial4Step7#9](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step7/vb/form1.vb#9)]  
  
     První řádek `if` jste právě přidali zkontroluje, zda v první popisek, který hráč vybere ikonu je stejná jako ikona druhého popisku. Pokud jsou ikony shodné, program provede tři příkazy mezi složenými závorkami v jazyce C# nebo tři příkazy v rámci `if` v sadě Visual Studio. První dva příkazy resetují `firstClicked` a `secondClicked` referenční proměnné tak, aby se už udržovat přehled o žádném popisku. (Tyto dva příkazy si možná pamatujete z obslužné rutiny události časovače Tick.) Třetí příkaz je `return` příkaz, který říká programu, aby přeskočil zbytek příkazů v metodě bez jejich spuštění.  
  
     Pokud programujete v jazyce Visual C#, mohli jste si všimnout, že některý kód používá jediný symbol rovnítka (`=`), zatímco jiné příkazy používají dva symboly rovná se (`==`). Zvažte, proč `=` se používá v některých místech, ale `==` je použit na dalších místech.  
  
     Toto je typický příklad, který ukazuje rozdíl. Pozorně se podívejte na kód mezi závorkami v `if` příkazu.  
  
    ```vb  
    firstClicked.Text = secondClicked.Text  
    ```  
  
    ```csharp  
    firstClicked.Text == secondClicked.Text  
    ```  
  
     Zkontrolujte pečlivě první příkaz v bloku kódu po `if` příkazu.  
  
    ```vb  
    firstClicked = Nothing  
    ```  
  
    ```csharp  
    firstClicked = null;  
    ```  
  
     První z těchto dvou příkazů ověří, zda jsou dvě ikony stejné. Protože se porovnávají dvě hodnoty, program Visual C# používá `==` operátor rovnosti. Druhý výpis skutečně změní hodnotu (volá *přiřazení*) a nastavte `firstClicked` referenční proměnnou rovna `null` resetovat ho. To je důvod, proč používá `=` operátor přiřazení místo. Visual C# používá `=` nastavit hodnoty, a `==` k jejich porovnání. Jazyk Visual Basic používá `=` pro přiřazení proměnné a porovnání.  
  
2.  Uložte a spusťte program a začněte vybírat ikony ve formuláři. Pokud zvolíte dvojici, která neodpovídá, událost časovače Tick se aktivuje a obě ikony zmizí. Pokud zvolíte odpovídající dvojici, nový `if` provede příkaz a návratový příkaz způsobí, že metoda vynechá kód, který spustí časovač, takže ikony zůstanou viditelné, jak je znázorněno na následujícím obrázku.  
  
     ![Hra, kterou vytvoříte v tomto kurzu](../ide/media/express-finishedgame.png "Express_FinishedGame")  
Porovnávací hra se zobrazenými dvojicemi ikon  
  
### <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat  
  
-   Přechod k dalšímu kroku výukového programu naleznete v tématu [krok 8: Přidejte metodu k ověření, zda the hráč zvítězil](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md).  
  
-   Chcete-li vrátit k předchozímu kroku tutoriálu, přečtěte si téma [krok 6: přidejte časovač](../ide/step-6-add-a-timer.md).



