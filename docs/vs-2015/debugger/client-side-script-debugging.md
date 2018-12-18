---
title: Ladění skriptů na straně klienta | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], client-side scripts
- client-side scripts, debugging
ms.assetid: bb668527-2288-47bd-a6c8-cecbad76dde2
caps.latest.revision: 33
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3aa04ab77b6e3dc6264a517c83c4ed319f36d686
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51817799"
---
# <a name="client-side-script-debugging"></a>Ladění skriptů na straně klienta
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ladicí program sady Visual Studio poskytuje všestranné prostředí pro nalezení a opravu chyb v klientských skriptech na stránkách ASP.NET.  
  
## <a name="opening-script-documents"></a>Otevření dokumentů skriptu  
 Můžete zobrazit seznamy dokumentů skriptů na straně serveru a na straně klienta v **Průzkumníka řešení** zobrazíte. Můžete otevřít libovolný dokument skriptu z **Průzkumníka řešení**. Další informace najdete v tématu [postupy: zobrazení dokumentů skriptu](../debugger/how-to-view-script-documents.md).  
  
## <a name="breakpoint-mapping"></a>Mapování zarážek  
 V sadě Visual Studio nelze přímo ladit kód na straně serveru, ale můžete nastavit zarážku v souboru na straně serveru. Visual Studio automaticky mapuje zarážku do odpovídajícího umístění v souboru straně klienta a vytvoří mapovanou zarážku v kódu na straně klienta.  
  
## <a name="manually-or-automatically-attaching-to-script"></a>Ruční nebo automatické připojení ke skriptu  
 Chcete-li začít ladit skript v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], ladicí program musí připojení ke skriptu, který chcete ladit. Může to ručně nebo automaticky.  
  
 Můžete provést ruční přiřazení pomocí [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozhraní ladicího programu k výběru spuštěného procesu skriptu, který chcete připojit k. Další informace najdete v tématu [postupy: připojení ke skriptu](../debugger/how-to-attach-to-script.md).  
  
 Ladicí program se automaticky připojí ke skriptu při jedné z následujících akcí:  
  
- Dostanete se ve skriptu nastavte zarážku.  
  
- Dosažení VBScript `Stop` příkazu nebo JScript `debugger` příkaz v kódu skriptu.  
  
- Prohlížeč a server zaznamená syntaxi nebo chybu při skriptu spuštění. Pokud k tomu dojde, dialogové okno se zobrazí a můžete začít ladění.  
  
  Pokud provedete ruční připojení ke skriptu, proces skriptování pokračuje, dokud není nějakým způsobem zastaven. Můžete ho zastavit výběrem **přerušit** na **ladění** nabídky.  
  
  Pokud ladicí program automaticky připojí, spuštění skriptu je zastaveno na řádku kde zarážka, `Stop` příkazu nebo `debugger` nebo chybu došlo k chybě, nebo v okamžiku, kdy jste se rozhodli spustit ladění v aplikaci Internet Explorer.  
  
  V tomto okamžiku můžete použít normální funkce ladicího programu a zahájit ladění. Například můžete použít **krok** příkazy pro další spouštění kódu řádek po řádku. Můžete použít **zásobník volání** okno k zobrazení a ovládání skript toku. Můžete použít okna proměnných nebo **okamžité** okno k zobrazení nebo změnu proměnných a vlastností.  
  
## <a name="enhanced-error-messages-for-script-debugging"></a>Rozšířené chybové zprávy pro ladění skriptů  
 Visual Studio poskytuje rozšířené chybové zprávy pro běžné potíže ladění skriptu. Tyto zprávy se nezobrazí, pokud se nepřipojíte k aplikaci Internet Explorer ručně. Pokud dojde k chybě při se automaticky otevře aplikace Internet Explorer, zkuste připojení ručně tak, aby se zobrazí chybové zprávy.  
  
## <a name="debugging-ajax-script-applications"></a>Ladění aplikací se skriptem AJAX  
 Webové aplikace s povoleným AJAX hojně používají kód skriptu a představují zvláštní problémy ladění. Informace o metodách ladění AJAX naleznete v tématu  
  
 [Ladění a trasování – přehled aplikace Ajax](http://msdn.microsoft.com/library/92684ea0-7bb4-4a34-9203-3aa6394ce375).  
  
## <a name="see-also"></a>Viz také  
 [Ladění aplikací ASP.NET a AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [Omezení ladění skriptů](../debugger/limitations-on-script-debugging.md)   
 [Proměnné Windows](http://msdn.microsoft.com/library/ce0a67f6-2502-4b7a-ba45-cc32f8aeba3e)   
 [Příkazové podokno](../ide/reference/immediate-window.md)   
 [Ladění a trasování – přehled jazyka Ajax aplikací](http://msdn.microsoft.com/library/92684ea0-7bb4-4a34-9203-3aa6394ce375)



