---
title: Ladění skriptů na straně klienta | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: 6405a35068b7be7ac93eb91f4d9100e6a840b0bb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65702383"
---
# <a name="client-side-script-debugging"></a>Ladění skriptů na straně klienta
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ladicí program sady Visual Studio poskytuje ucelené prostředí pro ladění pro hledání a opravy chyb na klientských skriptech na stránkách ASP.NET.  
  
## <a name="opening-script-documents"></a>Otevírání dokumentů skriptů  
 V **Průzkumník řešení** můžete zobrazit seznamy dokumentů skriptů na straně serveru a klienta. Můžete otevřít libovolný dokument skriptu z **Průzkumník řešení**. Další informace najdete v tématu [Postup: zobrazení dokumentů skriptu](../debugger/how-to-view-script-documents.md).  
  
## <a name="breakpoint-mapping"></a>Mapování zarážek  
 V sadě Visual Studio nemůžete přímo ladit kód na straně serveru, ale můžete nastavit zarážku v souboru na straně serveru. Visual Studio automaticky mapuje zarážku na odpovídající umístění v souboru na straně klienta a vytvoří namapovanou zarážku v kódu na straně klienta.  
  
## <a name="manually-or-automatically-attaching-to-script"></a>Ruční nebo automatické připojení ke skriptu  
 Chcete-li začít ladit skript v nástroji [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , ladicí program se musí připojit ke skriptu, který chcete ladit. K tomu může dojít ručně nebo automaticky.  
  
 K [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] výběru spouštěného procesu skriptu, ke kterému se chcete připojit, můžete ručně připojit pomocí rozhraní ladicího programu. Další informace najdete v tématu [Postup: připojení ke skriptu](../debugger/how-to-attach-to-script.md).  
  
 Ladicí program se ke skriptu automaticky připojí, když dojde k jedné z následujících akcí:  
  
- Ve skriptu budete mít nastavenou zarážku.  
  
- Ve vašem kódu skriptu jste narazili na příkaz jazyka VBScript `Stop` nebo příkaz jazyka JScript `debugger` .  
  
- V prohlížeči nebo serveru dojde k chybě syntaxe nebo chyby běhu ve skriptu. Pokud k tomu dojde, zobrazí se dialogové okno s možností spustit ladění.  
  
  Když se ručně připojíte ke skriptu, proces skriptu pokračuje v běhu, dokud není nějakým způsobem zastaven. Můžete ji zastavit výběrem možnosti **přerušit** v nabídce **ladění** .  
  
  Pokud se ladicí program automaticky připojí, spuštění skriptu je zastaveno na řádku, kde došlo k zarážce, `Stop` příkazu nebo `debugger` příkazu, nebo v místě, kde jste se rozhodli spustit ladění v aplikaci Internet Explorer.  
  
  V tomto okamžiku můžete k zahájení ladění použít normální zařízení ladicího programu. Například můžete použít příkazy **Step** pro pokračování v provádění kódu řádek po řádku. Okno **zásobník volání** můžete použít k zobrazení a řízení toku skriptu. K zobrazení nebo změně proměnných a vlastností lze použít okna proměnných nebo okno **Immediate** .  
  
## <a name="enhanced-error-messages-for-script-debugging"></a>Rozšířené chybové zprávy pro ladění skriptů  
 Visual Studio poskytuje rozšířené chybové zprávy pro běžné problémy ladění skriptu. Tyto zprávy se nezobrazí, pokud se k aplikaci Internet Explorer nepřipojíte ručně. Pokud dojde k chybě při automatickém otevření aplikace Internet Explorer, pokuste se připojit ručně, abyste mohli zobrazit chybové zprávy.  
  
## <a name="debugging-ajax-script-applications"></a>Ladění aplikací skriptu AJAX  
 Webové aplikace s podporou jazyka AJAX využívají těžké skriptovací kód a představují speciální výzvy k ladění. Informace o technikách ladění AJAX naleznete v tématu.  
  
 [Přehled ladění a trasování aplikací AJAX](https://msdn.microsoft.com/library/92684ea0-7bb4-4a34-9203-3aa6394ce375).  
  
## <a name="see-also"></a>Viz také  
 [Ladění aplikací ASP.NET a AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [Omezení ladění skriptů](../debugger/limitations-on-script-debugging.md)   
 [Okna proměnných](https://msdn.microsoft.com/library/ce0a67f6-2502-4b7a-ba45-cc32f8aeba3e)   
 [Příkazové okno](../ide/reference/immediate-window.md)   
 [Přehled ladění a trasování aplikací AJAX](https://msdn.microsoft.com/library/92684ea0-7bb4-4a34-9203-3aa6394ce375)
