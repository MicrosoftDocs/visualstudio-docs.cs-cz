---
title: Nativní Run-Time kontroluje vlastní nastavení | Microsoft Docs
description: 'Naučte se, jak přizpůsobit kontrolu za běhu, včetně: určení cíle zprávy, zápis funkce zasílání zpráv o chybách a dotazování na informace o chybě.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.crt
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- runtime_checks pragma
- debugger, native run-time checks
- /RTC compiler option [C++], native run-time checks
- customizing CRT error checking
- native run-time checks, customizing
ms.assetid: 76a365fe-6439-49db-8603-34058b78e5a8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 3b5f5aa55ac9d8c13da605a09986569c534a30bf
ms.sourcegitcommit: c67dece5ded82a5867148e1f94396954c1ec4398
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2021
ms.locfileid: "97975196"
---
# <a name="native-run-time-checks-customization"></a>Přizpůsobení nativních kontrol za běhu
Pokud kompilujete pomocí **/RTC** (kontroly za běhu) nebo použijete `runtime_checks` direktivu pragma, knihovna run-time jazyka C poskytuje nativní kontroly za běhu. V některých případech může být vhodné přizpůsobit kontrolu za běhu:

- Chcete-li směrovat zprávy o kontrole za běhu do souboru nebo jiného cíle než výchozí.

- Chcete-li určit cíl výstupu pro zprávy o kontrole za běhu v rámci ladicího programu třetí strany.

- Chcete-li ohlásit zprávy o kontrole za běhu z programu zkompilovaného pomocí prodejní verze knihovny run-time jazyka C. Verze vydaných verzí knihovny neslouží `_CrtDbgReportW` k nahlášení chyb modulu runtime. Namísto toho se zobrazí dialogové okno **kontrolní** výraz pro každou chybu za běhu.

  Chcete-li přizpůsobit kontrolu chyb v době běhu, můžete:

- Zápis funkce zasílání zpráv o chybách za běhu Další informace naleznete v tématu [How to: Write a Run-Time funkce zasílání zpráv o chybách](../debugger/how-to-write-a-run-time-error-reporting-function.md).

- Přizpůsobte cíl chybové zprávy.

- Dotaz na informace o chybách kontroly běhu.

## <a name="customize-the-error-message-destination"></a>Přizpůsobení cílového umístění chybové zprávy
 Pokud používáte `_CrtDbgReportW` k nahlášení chyb, můžete použít `_CrtSetReportMode` k určení cíle chybových zpráv.

 Pokud používáte vlastní funkci vytváření sestav, použijte `_RTC_SetErrorType` k přidružení chyby k typu sestavy.

## <a name="query-for-information-about-run-time-checks"></a>Dotaz na informace o kontrolách Run-Time
 `_RTC_NumErrors` Vrátí počet typů chyb zjištěných při kontrolách běhových chyb. Chcete-li získat stručný popis každé chyby, můžete provést smyčku z 0 na návratovou hodnotu `_RTC_NumErrors` a předáním hodnoty iterace do `_RTC_GetErrDesc` každé smyčky. Další informace najdete v tématu [_RTC_NumErrors](/cpp/c-runtime-library/reference/rtc-numerrors) a [_RTC_GetErrDesc](/cpp/c-runtime-library/reference/rtc-geterrdesc).

## <a name="see-also"></a>Viz také
- [Postupy: použití nativních kontrol Run-Time](../debugger/how-to-use-native-run-time-checks.md)
- [runtime_checks](/cpp/preprocessor/runtime-checks)
- [_CrtDbgReport, _CrtDbgReportW](/cpp/c-runtime-library/reference/crtdbgreport-crtdbgreportw)