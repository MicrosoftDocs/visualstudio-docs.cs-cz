---
title: Okno výstup | Dokumentace Microsoftu
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
- vs.build.output
- vs.debug.output
- vs.output
helpviewer_keywords:
- Output window, about Output window
- Output window
- Toolbox, removing controls
ms.assetid: d8931d88-250e-4db4-963f-2c5b3e99b45f
caps.latest.revision: 35
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 55869ff13cf4048b6d256e57892d470062847501
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49189901"
---
# <a name="output-window"></a>Okno Výstup
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
**Výstup** okna můžete zobrazit stavové zprávy pro různé funkce v integrovaném vývojovém prostředí (IDE). Chcete-li otevřít **výstup** okna na řádku nabídek zvolte **zobrazení/Output** (nebo klikněte na tlačítko CTRL + ALT + O).  
  
> [!WARNING]
>  V okně výstup nezobrazí v nabídce Zobrazit v edicích Visual Studio Express. Chcete-li ji vyvolat použijte klávesová zkratka CTRL + ALT + O.  
  
## <a name="toolbar"></a>Panel nástrojů  
 **Zobrazit výstup z:**  
 Zobrazí jednu nebo více výstupní podokna zobrazení. Několika podoken informace mohou být k dispozici, v závislosti na tom, jaké nástroje v integrovaném vývojovém prostředí používáte **výstup** okno doručení zprávy pro uživatele.  
  
 **Najít zprávu v kódu**  
 Přesune kurzor v editoru kódu k řádku, který obsahuje chybu vybrané sestavení.  
  
 **Přejít na předchozí zprávu**  
 Změní fokus v **výstup** okno na předchozí chyba sestavení a přesune kurzor v editoru kódu k řádku, který obsahuje sestavení chyby.  
  
 **Přejít na další zprávu**  
 Změní fokus v **výstup** okno na další chyba sestavení a přesune kurzor v editoru kódu k řádku, který obsahuje sestavení chyby.  
  
 **Vymazat vše**  
 Vymaže veškerý text z **výstup** podokně.  
  
 **Změnit zalamování řádků**  
 Zapne nebo vypne funkce zalamování **výstup** podokně. Po zabalení aplikace Word se na text v delší položky, která se rozpíná za oblast zobrazení se zobrazí na následující řádek.  
  
## <a name="output-pane"></a>Podokno výstup  
 **Výstup** vybrané v podokně **zobrazit výstup z:** seznamu se zobrazí výstup ze zdroje uvedené.  
  
## <a name="routing-messages-to-the-output-window"></a>Směrování zpráv do okna výstup  
 Pro zobrazení **výstup** okna pokaždé, když se v sestavení projektu, **Obecné, projekty a řešení, možnosti** dialogu **okně zobrazit výstup při spuštění sestavení**. Pak se soubor kódu otevřete pro úpravy, zvolte **přejít na další zprávu** a **přejít na předchozí zprávu** tlačítka na **výstup** panel nástrojů okna a vyberte položky v  **Výstup** podokně. Jak to provedete, kurzoru v kódu skoky editoru na řádek kódu, kde dochází k vybraný problém.  
  
 Některé funkce integrovaného vývojového prostředí a příkazech vyvolaných v [příkazové okno](../../ide/reference/command-window.md) dodávat svůj výstup do **výstup** okna. Výstup z externích nástrojů, jako jsou soubory .bat a .com, které se obvykle zobrazí v okně příkazového řádku, se rozšíří do **výstup** podokně vyberete **použití výstupním okně** možnost [Správa externích nástrojů](../../ide/managing-external-tools.md). Řadu dalších typů zpráv, které mohou být zobrazeny v **výstup** také podoken. Například když syntaxe jazyka Transact-SQL v uložené proceduře je porovnávána s cílovou databázi, výsledky se zobrazí v **výstup** okna.  
  
 Také můžete naprogramovat zapsat diagnostické zprávy v době běhu na vašich vlastních aplikací **výstup** podokně. K tomuto účelu použít členy <xref:System.Diagnostics.Debug> třídy nebo <xref:System.Diagnostics.Trace> třídy v <xref:System.Diagnostics> oboru názvů z knihovny tříd rozhraní .NET Framework. Členové <xref:System.Diagnostics.Debug> třídy zobrazit výstup při vytváření konfigurace ladění z řešení nebo projektu, členy <xref:System.Diagnostics.Trace> třídy zobrazit výstup při vytváření konfigurace ladění nebo vydání. Další informace najdete v tématu [diagnostické zprávy v okně výstupu](../../debugger/diagnostic-messages-in-the-output-window.md).  
  
 V [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)], můžete vytvořit vlastní kroky sestavení a události sestavení, jejichž upozornění a chyby se zobrazí a jsou počítány v **výstup** podokně. Stisknutím klávesy F1 v řádku výstupu, můžete zobrazit příslušné téma nápovědy. Další informace najdete v tématu [Formátovaní výstupu vlastního kroku sestavení nebo události sestavení](http://msdn.microsoft.com/library/92ad3e38-24d7-4b89-90e6-5a16f5f998da).  
  
## <a name="scrolling-behavior"></a>Chování posouvání  
 Pokud používáte automatické procházení v okně Výstup a potom přejděte pomocí myši nebo šipka klíčů, zastaví se automatické procházení. Pokud chcete obnovit automatické procházení, stisknutím klávesy CTRL + END.  
  
## <a name="see-also"></a>Viz také  
 [Diagnostické zprávy v okně Výstup](../../debugger/diagnostic-messages-in-the-output-window.md)   
 [Postupy: řízení výstupního okna](http://msdn.microsoft.com/library/91aebd15-8854-4a7a-9f7d-57376fb4e858)   
 [Kompilování a sestavování](../../ide/compiling-and-building-in-visual-studio.md)   
 [Principy konfigurací sestavení](../../ide/understanding-build-configurations.md)   
 [Přehled knihovny tříd](http://msdn.microsoft.com/library/7e4c5921-955d-4b06-8709-101873acf157)



