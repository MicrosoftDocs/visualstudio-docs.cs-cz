---
title: 'Testovací oblast 6: Odstranění | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source control [Visual Studio SDK], deleting items
- source control plug-ins, deleting items
ms.assetid: 6f2e872c-5ba2-4303-9f50-a90cef9a6225
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1498566e1afeaf1517b7ae3bd62297444c828888
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51766311"
---
# <a name="test-area-6-delete"></a>Testovací oblast 6: Odstranění
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Tato oblast testovací modul plug-in správy zdrojového kódu zahrnuje akce odstranění.  
  
 Ovládací prvek zdroje reaguje na akce v odstranění **Průzkumníka řešení**.  
  
 Tady je seznam položek, které je možné odstranit:  
  
- Soubory  
  
- Složky  
  
- Projekt  
  
  V závislosti na typu projektu, může mít možnost **odebrat** projektu (ponechá soubory na disku) nebo **odstranit** projektu (odebere soubory na disku). Obě akce odebere projekt nebo položku z **Průzkumníka řešení**.  
  
## <a name="expected-behavior"></a>Očekávané chování  
 Očekávané chování u testovací případy v testovací oblast odstranění je:  
  
-   Odstraněné položky už nejsou viditelné v rámci **Průzkumníka řešení**.  
  
-   Nadřazený odstraněný projekt nebo položku je rezervován podle potřeby (případně s výzvou.)  
  
-   Po odstranění rezervovaný nebo položka se přidala, se nezobrazí v **čekající vrácení se změnami** okna.  
  
-   Položka stále existuje v rámci úložiště správy zdrojových kódů, i po jejím odstranění a musí být ručně odstraněna.  
  
|Akce|Testovací kroky|Chcete-li ověřit očekávané výsledky|  
|------------|----------------|--------------------------------|  
|Odstranit klientský projekt|1.  Vytvoření projektu klienta.<br />2.  Přidáte řešení do správy zdrojového kódu.<br />3.  Odebrat celý projekt z řešení|Běžné očekávané chování.|  
|Odstranit prázdný soubor|1.  Vytvoření projektu klienta.<br />2.  Do projektu přidat soubor nula bajtů.<br />3.  Přidáte řešení do správy zdrojového kódu.<br />4.  Vyberte soubor, odstraňte ho.|Běžné očekávané chování.|  
|Odstranit složku s jedním souborem|1.  Vytvořte řešení pro jeden projekt.<br />2.  Přidáte složku.<br />3.  Přidejte jeden soubor do složky.<br />4.  Přidáte řešení do správy zdrojového kódu.<br />5.  Podívejte se na projekt tak, aby se zabránilo zobrazí výzvu.<br />6.  Odstraňte složku.|Běžné očekávané chování.|  
|Odstranit projekt webového systému souborů|1.  Vytvoření webového systému souboru projektu (pomocí tlačítka Procházet k určení cesty UNC).<br />2.  Přidáte řešení do správy zdrojového kódu.<br />3.  Odeberte celý projekt z řešení.<br />4.  Opakujte kroky 1 až 3 pro místní webový projekt (vykonává různých cest skrze kód, ale má stejné externí rozhraní a chování).|Běžné očekávané chování.|  
|Odstranit soubor z webového systému souboru projektu|1.  Vytvoření webového systému souboru projektu.<br />2.  Přidáte řešení do správy zdrojového kódu.<br />3.  Odstranění souboru z projektu.<br />4.  Opakujte kroky 1 až 3 pro místní webový projekt (vykonává různých cest skrze kód, ale má stejné externí rozhraní a chování).|Běžné očekávané chování.|  
  
## <a name="see-also"></a>Viz také  
 [Testovací příručka pro moduly plug-in správy zdrojového kódu](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)

