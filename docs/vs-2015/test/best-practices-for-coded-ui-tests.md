---
title: Osvědčené postupy pro programové testy UI | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- coded UI tests, best practices
ms.assetid: d5aef766-a24c-4f1f-ac9b-e5462b6627d4
caps.latest.revision: 41
ms.author: gewarren
manager: douge
ms.openlocfilehash: 1a067751662895f99f4caf95d487dc8c8a4672f3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49903579"
---
# <a name="best-practices-for-coded-ui-tests"></a>Doporučené postupy pro programové testy UI
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Toto téma popisuje doporučené postupy při vývoji programové testy uživatelského rozhraní.  
  
 **Požadavky**  
  
-   Visual Studio Enterprise  
  
## <a name="best-practices"></a>Doporučené postupy  
 Pomocí následujících pokynů k vytvoření flexibilní programový test uživatelského rozhraní.  
  
- Použití **Tvůrce programového testu UI** kdykoli je to možné.  
  
- Neprovádějte žádné změny `UIMap.designer.cs` přímo soubor. Pokud to uděláte, změny do souboru budou přepsány.  
  
- Vytvoření testu jako posloupnost nahrané metody. Další informace o tom, jak zaznamenat metodu, najdete v části [vytváření programových testů UI](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate).  
  
- Každý zaznamenanou metodu by měl fungovat na jednu stránku, formulář nebo dialogové okno. Vytvoření nové metody testu pro každou novou stránku, formulář nebo dialogové okno.  
  
- Při vytváření metody, použijte název smysluplné metoda místo výchozí název. Smysluplný název pomáhá identifikovat cílem této metody.  
  
- Pokud je to možné, omezte každý zaznamenanou metodu na míň než 10 akce. Tento přístup modulární usnadňuje nahraďte metodu, pokud se změní uživatelské rozhraní.  
  
- Vytvoření s použitím každého kontrolního výrazu **Tvůrce programového testu UI**, která automaticky přidá metodu kontrolního výrazu k `UIMap.Designer.cs` souboru.  
  
- Pokud se změní uživatelské rozhraní (UI), znovu nahrávat testovací metody nebo výrazu metody nebo znovu nahrávat ovlivněné oddíly stávající testovací metody.  
  
- Vytvořit samostatnou <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap> soubor pro každý modul v testované aplikaci. Další informace najdete v tématu [testování rozsáhlé aplikace s více mapami uživatelského rozhraní](../test/testing-a-large-application-with-multiple-ui-maps.md).  
  
- V testované aplikaci, použijte smysluplné názvy při vytváření ovládacích prvků uživatelského rozhraní. To poskytuje další význam a použitelnost k automaticky vygenerovanému ovládacímu prvku názvy.  
  
- Kontrolní výrazy při vytváření kódu pomocí rozhraní API, vytvořte metodu pro každého kontrolního výrazu v části <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap> třídu, která je v `UIMap.cs` souboru. Tuto metodu volejte z testovací metody k provedení kontrolního výrazu.  
  
- Pokud píšete kód přímo s rozhraním API, použijte vlastnosti a metody do třídy vygenerované v `UIMap.Designer.cs` souborů ve vašem kódu tak, jak můžete. Tyto třídy provede svou práci, jednodušší a spolehlivější a vám pomohou být produktivnější.  
  
  Programové testy uživatelského rozhraní automaticky přizpůsobit mnoho změn v uživatelském rozhraní. Pokud například prvek uživatelského rozhraní došlo ke změně umístění a barvy, ve většině případů programový test UI najít správný element.  
  
  Během testovacího běhu, ovládacích prvků uživatelského rozhraní jsou umístěné v rámci testovacího rozhraní sady vyhledávání vlastností, které se použijí na každou třídu ovládacího prvku v definicích vytvořené **Tvůrce programového testu UI** v `UIMap.Designer.cs` souboru. Vlastnosti hledání obsahují páry název hodnota názvů vlastností a hodnot vlastností, které slouží k identifikaci ovládacího prvku, například <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.FriendlyName%2A>, <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.Name%2A>, a <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.ControlType%2A> vlastnosti ovládacího prvku. Pokud jsou beze změny vlastnosti vyhledávání, programový test uživatelského rozhraní úspěšně najít ovládací prvek v uživatelském rozhraní. Pokud se změní vlastnosti hledání, musí programové testy UI inteligentní shody algoritmu, který použije heuristiku k nalezení ovládací prvky a windows v uživatelském rozhraní. Pokud došlo ke změně uživatelského rozhraní, je možné upravit vlastnosti hledání dříve zjištěné prvků, abyste měli jistotu, že se nenachází.  
  
## <a name="what-to-do-if-your-user-interface-changes"></a>Co dělat, když se změní vaše uživatelské rozhraní  
 Uživatelské rozhraní se často měnit během vývoje. Tady jsou některé způsoby, aby se snížil dopad těchto změn:  
  
- Najít zaznamenanou metodu, která odkazuje na tento ovládací prvek a použijte **Tvůrce programového testu UI** na opakovat záznam akce pro tuto metodu. Přepsat existující akce můžete použít stejný název pro metodu.  
  
- Pokud má ovládací prvek, který již není platný kontrolní výraz:  
  
  -   Odstraníte metodu, která obsahuje kontrolní výraz.  
  
  -   Odeberte volání této metody z testovací metody.  
  
  -   Přidat kontrolní výraz nové přetažením nitkového kříže tlačítko na ovládací prvek uživatelského rozhraní, otevřete v mapování uživatelského rozhraní a přidat nový kontrolní výraz.  
  
  Další informace o tom, jak zaznamenat programové testy UI, naleznete v tématu [pomocí uživatelského rozhraní automatizace k testu kódu](../test/use-ui-automation-to-test-your-code.md).  
  
## <a name="what-to-do-if-a-background-process-needs-to-complete-before-the-test-can-continue"></a>Co dělat, když proces na pozadí musí dokončit před pokračováním v testu  
 Budete muset počkat, dokud se proces dokončí, než budete pokračovat s další akce uživatelského rozhraní. K tomu můžete použít <xref:Microsoft.VisualStudio.TestTools.UITesting.PlaybackSettings.WaitForReadyLevel%2A> čekat, než testu bude pokračovat stejně jako v následujícím příkladu.  
  
```  
// Set the playback to wait for all threads to finish  
Playback.PlaybackSettings.WaitForReadyLevel = WaitForReadyLevel.AllThreads;  
  
// Press the submit button  
this.UIMap.ClickSubmit();  
  
// Reset the playback to wait only for the UI thread to finish  
Playback.PlaybackSettings.WaitForReadyLevel = WaitForReadyLevel.UIThreadOnly;  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap>   
 <xref:Microsoft.VisualStudio.TestTools.UITesting>   
 [Použití automatizace uživatelského rozhraní k testování kódu](../test/use-ui-automation-to-test-your-code.md)   
 [Vytváření programových testů UI](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate)   
 [Testování rozsáhlé aplikace s více mapami uživatelského rozhraní](../test/testing-a-large-application-with-multiple-ui-maps.md)   
 [Podporované konfigurace a platformy pro programové testy uživatelského rozhraní a zaznamenávání akcí](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)



