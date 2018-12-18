---
title: COM Server a ladění kontejneru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.com
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- ActiveX control container debugging [Visual Studio]
- debugging ActiveX controls
- COM servers, debugging
- ActiveX controls, debugging
- COM [Visual Studio], debugging
ms.assetid: b7ce8696-ebb8-4354-a767-f76b8ada4ac1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5b4c23d362a930f28ccb1a097de44a936e55cacf
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2018
ms.locfileid: "31458174"
---
# <a name="com-server-and-container-debugging"></a>Ladění serveru a kontejneru modelu COM
Aplikace modelu COM provést určité úlohy mimo pro programátory přímou kontrolu. Komunikace mezi knihovny DLL, využití počítá na objekty a operace se schránkou je uvedeno několik z oblastí, kde může dojít k neočekávanému chování. Pokud k tomu dojde, je prvním krokem sledovat zdroj problému.  
  
 Ladicí program Visual Studio podporuje krokování s napříč a do kontejnery a servery. To zahrnuje možnost krok napříč vzdálených volání procedur (RPC).  
  
##  <a name="BKMK_COMServerandContainerintheSameSolution"></a> Ladění kontejneru ve stejném řešení a COM Server  
 Můžete ladit COM server a kontejneru pomocí dva projekty v řešení bude stejné. Nastavte zarážky příslušné v každém projektu a ladění. Když kontejneru provede volání do serveru, který dotkne zarážku, kontejner bude čekat, dokud serverový kód vrátí (to znamená, dokud nedokončíte, ladění).  
  
 Ladění kontejnerů COM je podobná ladění standardní program. Jeden rozdíl je při ladění událost, která generuje zpětné volání (například přetahování dat prostřednictvím aplikací kontejneru). V takovém případě musíte nastavit zarážky ve funkci zpětného volání.  
  
##  <a name="BKMK_ServerApplicationWithoutContainerInformation"></a> Ladění aplikace serveru bez informace o kontejneru  
 Pokud nemají nebo nechcete použít informace o ladění pro aplikace kontejneru, spouštění k ladění aplikací serveru je proces třech krocích:  
  
1.  Spusťte ladění serveru jako normální aplikace.  
  
2.  Nastavte zarážky podle potřeby.  
  
3.  Spusťte aplikaci kontejneru.  
  
##  <a name="BKMK_DebuggingaServerandDomainIsolationSDIApplication"></a> Ladění serveru a aplikace (SDI) izolace domény  
 Pokud ladíte aplikace serveru SDI, je nutné zadat `/Embedding` nebo `/Automation` v **argumenty příkazového řádku** vlastnost *projektu* dialogové okno stránky vlastností pro C/C++, C#, nebo Projekty Visual Basic.  
  
 S těmito argumenty příkazového řádku můžete ladicí program spustit serverové aplikace, jako by se měla spustit z kontejneru. Kontejner od programu Správce nebo správce souborového způsobí kontejneru pro použití instance serveru spuštěna v ladicím programu.  
  
 Abyste měli přístup *projektu* dialogové okno stránky vlastností, klikněte pravým tlačítkem na projekt v Průzkumníku řešení a potom v místní nabídce vyberte možnost Vlastnosti. Chcete-li najít vlastnost argumenty příkazového řádku, rozbalte kategorii vlastnosti konfigurace a klikněte na stránce ladění.  
  
## <a name="see-also"></a>Viz také  
 [COM a prvků ActiveX ladění](../debugger/com-and-activex-debugging.md)