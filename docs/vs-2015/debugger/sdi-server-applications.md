---
title: Serverové aplikace SDI | Microsoft Docs
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
- SDI server applications
- SDI server applications, debugging
ms.assetid: 09713718-1376-4753-b119-26f36639693e
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1296c0f43d0409df0081861095c5ec068932bbc1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148151"
---
# <a name="sdi-server-applications"></a>Aplikace serveru SDI
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pokud ladíte serverovou aplikaci SDI, je nutné zadat `/Embedding` nebo `/Automation` do vlastnosti **argumenty příkazového řádku** v dialogovém okně stránky vlastností *projektu* pro projekty C/C++, C# nebo Visual Basic.  
  
 Pomocí těchto argumentů příkazového řádku může ladicí program spustit serverovou aplikaci, jako kdyby byla spuštěna z kontejneru. Spuštění kontejneru z programu Správce programů nebo správce souborů způsobí, že se v kontejneru použije instance serveru spuštěného v ladicím programu.  
  
## <a name="finding-the-command-line-arguments-property"></a>Hledání vlastnosti argumentů příkazového řádku  
 Chcete-li získat přístup k dialogovému oknu stránky vlastností *projektu* , klikněte pravým tlačítkem myši na projekt v Průzkumník řešení a potom v místní nabídce vyberte možnost Vlastnosti. Chcete-li najít vlastnost argumenty příkazového řádku, rozbalte kategorii vlastnosti konfigurace a klikněte na stránku ladění.  
  
## <a name="see-also"></a>Viz také  
 [Ladění modelu COM a ActiveX](../debugger/com-and-activex-debugging.md)   
 [Postupy: ladění serverů modelu COM](../debugger/how-to-debug-com-servers.md)
