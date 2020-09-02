---
title: Přizpůsobení nativních kontrol za běhu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.crt
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- runtime_checks pragma
- debugger, native run-time checks
- /RTC compiler option [C++], native run-time checks
- customizing CRT error checking
- native run-time checks, customizing
ms.assetid: 76a365fe-6439-49db-8603-34058b78e5a8
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 434f2425b1eeefd82b954e47a8ced55491a7ec11
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697811"
---
# <a name="native-run-time-checks-customization"></a>Přizpůsobení nativních kontrol za běhu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pokud kompilujete pomocí **/RTC** (kontroly za běhu) nebo použijete `runtime_checks` direktivu pragma, knihovna run-time jazyka C poskytuje nativní kontroly za běhu. V některých případech může být vhodné přizpůsobit kontrolu za běhu:  
  
- Chcete-li směrovat zprávy o kontrole za běhu do souboru nebo jiného cíle než výchozí.  
  
- Chcete-li určit cíl výstupu pro zprávy o kontrole za běhu v rámci ladicího programu třetí strany.  
  
- Chcete-li ohlásit zprávy o kontrole za běhu z programu zkompilovaného pomocí prodejní verze knihovny run-time jazyka C. Verze vydaných verzí knihovny neslouží `_CrtDbgReportW` k nahlášení chyb modulu runtime. Namísto toho se zobrazí dialogové okno **kontrolní** výraz pro každou chybu za běhu.  
  
  Chcete-li přizpůsobit kontrolu chyb v době běhu, můžete:  
  
- Zápis funkce zasílání zpráv o chybách za běhu Další informace naleznete v tématu [Postupy: zápis funkce zasílání zpráv o chybách za běhu](../debugger/how-to-write-a-run-time-error-reporting-function.md).  
  
- Přizpůsobte cíl chybové zprávy.  
  
- Dotaz na informace o chybách kontroly běhu.  
  
## <a name="customize-the-error-message-destination"></a>Přizpůsobení cílového umístění chybové zprávy  
 Pokud používáte `_CrtDbgReportW` k nahlášení chyb, můžete použít `_CrtSetReportMode` k určení cíle chybových zpráv.  
  
 Pokud používáte vlastní funkci vytváření sestav, použijte `_RTC_SetErrorType` k přidružení chyby k typu sestavy.  
  
## <a name="query-for-information-about-run-time-checks"></a>Dotaz na informace o kontrolách běhu  
 `_RTC_NumErrors` Vrátí počet typů chyb zjištěných při kontrolách běhových chyb. Chcete-li získat stručný popis každé chyby, můžete provést smyčku z 0 na návratovou hodnotu `_RTC_NumErrors` a předáním hodnoty iterace do `_RTC_GetErrDesc` každé smyčky. Další informace najdete v tématu [_RTC_NumErrors](https://msdn.microsoft.com/library/7e82adae-38e2-4f8b-bc0b-37bda8109fd1) a [_RTC_GetErrDesc](https://msdn.microsoft.com/library/7994ec2b-5488-4fd4-806d-a166c9a9f927).  
  
## <a name="see-also"></a>Viz také  
 [Postupy: použití nativních kontrol za běhu](../debugger/how-to-use-native-run-time-checks.md)   
 [runtime_checks](https://msdn.microsoft.com/library/ae50b43f-f88d-47ad-a2db-3389e9e7df5b)   
 [_CrtDbgReport, _CrtDbgReportW](https://msdn.microsoft.com/library/6e581fb6-f7fb-4716-9432-f0145d639ecc)
