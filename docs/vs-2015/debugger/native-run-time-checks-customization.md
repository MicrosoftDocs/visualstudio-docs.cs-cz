---
title: Nativní Run-Time kontroluje přizpůsobení | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: 216a96a6702bfabc57d235144bf4a6cc05df4224
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51721140"
---
# <a name="native-run-time-checks-customization"></a>Přizpůsobení nativních kontrol za běhu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pokud kompilujete s **/RTC** (kontroly za běhu) nebo použít `runtime_checks` – Direktiva pragma, knihovny run-time jazyka C poskytuje nativní kontroly za běhu. V některých případech můžete chtít přizpůsobit kontrolu za běhu:  
  
- Můžete směrovat zprávy kontrola běhu soubor nebo cíl jiné než výchozí.  
  
- K určení výstupní cíl pro za běhu kontrolovat zprávy v ladicím programu třetích stran.  
  
- K hlášení kontroly za běhu z programu kompilovaného s verzi knihovny run-time C. Verze knihovny nepoužívejte `_CrtDbgReportW` pro hlášení chyb za běhu. Zobrazí se místo toho **Assert** dialogové okno u každé chyby za běhu.  
  
  Chcete-li přizpůsobit, kontrola chyb za běhu, můžete:  
  
- Zápis chyb za běhu funkce vytváření sestav. Další informace najdete v tématu [postupy: zápis funkce generování sestav chyb za běhu](../debugger/how-to-write-a-run-time-error-reporting-function.md).  
  
- Upravte cíl chybové zprávy.  
  
- Dotaz na informace o běhu najdete v chybách.  
  
## <a name="customize-the-error-message-destination"></a>Upravit cíl chybové zprávy  
 Pokud používáte `_CrtDbgReportW` pro hlášení chyb, můžete použít `_CrtSetReportMode` k určení cíle chybové zprávy.  
  
 Pokud používáte vlastní funkci vykazování, použijte `_RTC_SetErrorType` chcete přidružit k chybě typu sestavy.  
  
## <a name="query-for-information-about-run-time-checks"></a>Dotaz na informace o kontrolách za běhu  
 `_RTC_NumErrors` Vrátí počet typů chyb zjištěných kontroly chyb za běhu. Získáte stručný popis jednotlivých chyb můžete opakování od 0 do návratová hodnota `_RTC_NumErrors`, předejte hodnotu iterace k `_RTC_GetErrDesc` na každou smyčku. Další informace najdete v tématu [_rtc_numerrors –](http://msdn.microsoft.com/library/7e82adae-38e2-4f8b-bc0b-37bda8109fd1) a [_RTC_GetErrDesc](http://msdn.microsoft.com/library/7994ec2b-5488-4fd4-806d-a166c9a9f927).  
  
## <a name="see-also"></a>Viz také  
 [Postupy: použití nativních kontrol za běhu](../debugger/how-to-use-native-run-time-checks.md)   
 [runtime_checks –](http://msdn.microsoft.com/library/ae50b43f-f88d-47ad-a2db-3389e9e7df5b)   
 [_CrtDbgReport, _CrtDbgReportW](http://msdn.microsoft.com/library/6e581fb6-f7fb-4716-9432-f0145d639ecc)





