---
title: 'Krok 4: Přidejte metodu CheckTheAnswer() | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c66f3831-b4a0-40bc-a109-8f46f4db35ed
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: cf3f58e9d597af067db9e5d3037a78572a1528ef
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49181106"
---
# <a name="step-4-add-the-checktheanswer-method"></a>Krok 4: Přidejte metodu CheckTheAnswer()
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ve čtvrté části tohoto tutoriálu budete zapisovat metodu `CheckTheAnswer()`, která určuje, zda jsou odpovědi na matematické úlohy správné. Toto téma je součástí série kurzů o základních principech kódování. Přehled kurzu, naleznete v tématu [kurz 2: vytvoření a Timed Math Quiz](../ide/tutorial-2-create-a-timed-math-quiz.md).  
  
> [!NOTE]
>  Pokud jste postupovali v jazyce Visual Basic, budete používat `Function` – klíčové slovo namísto obvyklého `Sub` – klíčové slovo vzhledem k tomu, že tato metoda vrátí hodnotu. Je skutečně tak jednoduché: sub nevrací hodnotu, ale funkce Ano.  
  
### <a name="to-verify-whether-the-answers-are-correct"></a>Chcete-li ověřit, zda jsou odpovědi správné  
  
1.  Přidat `CheckTheAnswer()` metody.  
  
     Když tato metoda je volána, přidá hodnoty addend1 a addend2 a porovnává výsledek s hodnotou v součtu `NumericUpDown` ovládacího prvku. Pokud jsou hodnoty stejné, vrátí metoda hodnotu `true`. Jinak metoda vrátí hodnotu `false`. Váš kód by měl vypadat nějak takto.  
  
     [!code-csharp[VbExpressTutorial3Step4#8](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step4/cs/form1.cs#8)]
     [!code-vb[VbExpressTutorial3Step4#8](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step4/vb/form1.vb#8)]  
  
     Dále zkontrolujte odpověď aktualizací kódu v metodě pro obslužnou rutinu události Tick časovače pro zavolání nové `CheckTheAnswer()` metody.  
  
2.  Přidejte následující kód, který `if else` příkazu.  
  
     [!code-csharp[VbExpressTutorial3Step4#10](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step4/cs/form1.cs#10)]
     [!code-vb[VbExpressTutorial3Step4#10](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step4/vb/form1.vb#10)]  
  
     Pokud je odpověď správná, `CheckTheAnswer()` vrátí `true`. Obslužná rutina události zastaví časovač, zobrazí zprávu s gratulací a pak **Start** opět zpřístupní tlačítko. V opačném případě kvíz pokračuje.  
  
3.  Uložte program, spusťte ho, spusťte kvíz a zadejte správnou odpověď úlohu sčítání.  
  
    > [!NOTE]
    >  Když zadáte vaši odpověď, musíte buď vybrat výchozí hodnotu, než začnete zadávat odpověď nebo musíte nulu odstranit ručně. Opravu tohoto chování provedeme dále v tomto kurzu.  
  
     Pokud zadáte správnou odpověď, otevře se okno se zprávou, **Start** tlačítko bude k dispozici a časovač se zastaví.  
  
### <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat  
  
-   Přechod k dalšímu kroku výukového programu naleznete v tématu [krok 5: přidejte zadejte obslužné rutiny událostí pro ovládací prvky NumericUpDown](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md).  
  
-   Chcete-li vrátit k předchozímu kroku tutoriálu, přečtěte si téma [krok 3: přidejte časovač odpočítávání](../ide/step-3-add-a-countdown-timer.md).



