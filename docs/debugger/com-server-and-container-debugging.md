---
title: Ladění serveru a kontejneru modelu COM | Microsoft Docs
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ec5ed51c72ad7fd64bbdfd0135f53a13bb8c6e4b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72745678"
---
# <a name="com-server-and-container-debugging"></a>Ladění serveru a kontejneru modelu COM
Aplikace modelu COM provádějí řadu úkolů mimo přímo ovládací prvek programátora. Komunikace mezi knihovnami DLL, počty využití objektů a operacemi ve schránce jsou pouze v několika oblastech, ve kterých se může narazit na neočekávané chování. Pokud k tomu dojde, je vaším prvním krokem sledování zdroje problému.

 Ladicí program sady Visual Studio podporuje krokování napříč a do kontejnerů a serverů. To zahrnuje možnost Krokovat přes vzdálené volání procedur (RPC).

## <a name="debugging-a-com-server-and-container-in-the-same-solution"></a><a name="BKMK_COMServerandContainerintheSameSolution"></a> Ladění serveru a kontejneru modelu COM ve stejném řešení
 Můžete ladit server COM a kontejner pomocí dvou projektů v rámci jednoho řešení. Nastavte odpovídající zarážky v každém projektu a proveďte ladění. Když kontejner provede volání do serveru, který narazí na zarážku, kontejner počká, až vrátí serverový kód (tj. dokud nedokončíte ladění).

 Ladění kontejneru COM je podobné jako ladění standardního programu. Jeden rozdíl je při ladění události, která generuje zpětné volání (například přetahování dat přes aplikaci kontejneru). V takovém případě musíte nastavit zarážku ve funkci zpětného volání.

## <a name="debugging-a-server-application-without-container-information"></a><a name="BKMK_ServerApplicationWithoutContainerInformation"></a> Ladění serverové aplikace bez informací o kontejneru
 Pokud nemáte nebo nechcete používat informace o ladění pro aplikaci typu kontejner, začněte ladit serverovou aplikaci pomocí procesu se třemi kroky:

1. Spusťte ladění serveru jako normální aplikace.

2. Nastavte zarážky podle potřeby.

3. Spusťte aplikaci kontejneru.

## <a name="debugging-a-server-and-domain-isolation-sdi-application"></a><a name="BKMK_DebuggingaServerandDomainIsolationSDIApplication"></a> Ladění aplikace pro izolaci serverů a domén (SDI)
 Pokud ladíte serverovou aplikaci SDI, je nutné zadat `/Embedding` nebo `/Automation` do vlastnosti **argumenty příkazového řádku** v dialogovém okně stránky vlastností *projektu* pro projekty C/C++, C# nebo Visual Basic.

 Pomocí těchto argumentů příkazového řádku může ladicí program spustit serverovou aplikaci, jako kdyby byla spuštěna z kontejneru. Spuštění kontejneru z programu Správce programů nebo správce souborů způsobí, že se v kontejneru použije instance serveru spuštěného v ladicím programu.

 Chcete-li získat přístup k dialogovému oknu stránky vlastností *projektu* , klikněte pravým tlačítkem myši na projekt v Průzkumník řešení a potom v místní nabídce vyberte možnost Vlastnosti. Chcete-li najít vlastnost argumenty příkazového řádku, rozbalte kategorii vlastnosti konfigurace a klikněte na stránku ladění.

## <a name="see-also"></a>Viz také

- [Ladění modelů COM a prvků ActiveX](../debugger/com-and-activex-debugging.md)