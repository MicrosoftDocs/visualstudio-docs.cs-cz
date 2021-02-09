---
title: Diagnostická data a systémem generované protokoly
description: Přečtěte si o protokolech generovaných systémem Visual Studio, typech shromažďovaných dat a o tom, jak se používají k řešení problémů a zlepšení kvality produktu.
ms.custom: SEO-VS-2020
ms.date: 05/24/2018
ms.topic: conceptual
author: jillre
ms.author: michma
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7a6df4a90d8ddb31db88bb91ff4e874cadd3c589
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99894657"
---
# <a name="system-generated-logs-collected-by-visual-studio"></a>Systémem generované protokoly shromážděné aplikací Visual Studio

Visual Studio shromažďuje systémem generované protokoly, aby opravila problémy a vylepšila kvalitu produktu prostřednictvím program Zlepšování softwaru a služeb na základě zkušeností uživatelů sady [Visual Studio](visual-studio-experience-improvement-program.md). Tento článek poskytuje některé informace o typech shromažďovaných dat a o tom, jak ji používáme. Poskytuje také tipy, jak mohou autoři rozšíření zabránit nechtěnému zveřejnění osobních nebo citlivých informací.

## <a name="types-of-collected-data"></a>Typy shromážděných dat

Visual Studio shromažďuje systémem generované protokoly chyb, nereagující z uživatelského rozhraní a vysokého využití procesoru nebo paměti. Shromažďujeme také informace o chybách, ke kterým došlo při instalaci nebo použití produktu. Shromážděná data se liší v závislosti na chybě a mohou zahrnovat trasování zásobníku, výpisy paměti a informace o výjimce:

- Pro zajištění vysokého využití procesoru a nereagují se shromažďují záznamy zásobníku relevantních vláken sady Visual Studio.

- V případě, že trasování zásobníku některých vláken nestačí k určení původní příčiny problému, například chyby, nereagující nebo vysoké využití paměti, shromažďujeme *Výpis* paměti. Výpis stavu paměti představuje stav procesu, kdy došlo k chybě.

- V případě neočekávaných chybových stavů, například při pokusu o zápis do souboru na disku, shromažďujeme informace o výjimce. Informace obsahují název výjimky, trasování zásobníku vlákna, kde došlo k výjimce, zprávu spojenou s výjimkou a další informace, které jsou relevantní pro konkrétní výjimku.

   Následující příklad shromážděných dat zobrazuje název výjimky, trasování zásobníku a zprávu o výjimce:

   ```text
   "Reserved.DataModel.Fault.Exception.TypeString": "System.IO.IOException",
   "Reserved.DataModel.Fault.Exception.StackTrace": "System.IO.__Error.WinIOError(Int32,String)\r\n
   System.IO.FileStream.Init(String,FileMode,FileAccess,Int32,Boolean,FileShare,Int32,FileOptions,SECURITY_ATTRIBUTES,String,Boolean,Boolean,Boolean)\r\n
   System.IO.FileStream..ctor(String,FileMode,FileAccess,FileShare,Int32,FileOptions,String,Boolean,Boolean,Boolean)\r\nSystem.IO.StreamWriter.CreateFile(String,Boolean,Boolean)\r\n
   System.IO.StreamWriter..ctor(String,Boolean,Encoding,Int32,Boolean)\r\n
   System.IO.StreamWriter..ctor(String,Boolean)\r\n
   System.IO.File.CreateText(String)\r\n
   Microsoft.VisualStudio.Setup.Services.FileSystem.CreateText(String,Boolean)\r\n
   Microsoft.VisualStudio.Setup.Cache.ChannelManifestRepository.WriteChannelManifest(IChannelManifest,String,String)\r\n
   Microsoft.VisualStudio.Setup.Cache.ChannelManifestRepository.AddChannel(ChannelManifestPair,Boolean)\r\n
   Microsoft.VisualStudio.Setup.Cache.CacheManager.AddChannel(ChannelManifestPair,Boolean)\r\n
   Microsoft.VisualStudio.Setup.ChannelManager.\<UpdateAsync>d__37.MoveNext()\r\n”,
   "Reserved.DataModel.Fault.Exception.Message": " The process cannot access the file 'C:\\Users\\[UserName]\\AppData\\Local\\Microsoft\\VisualStudio\\Packages\\_Channels\\4CB340F5\\channelManifest.json' because it is being used by another process."
   ```

## <a name="how-we-use-system-generated-logs"></a>Jak používat systémem generované protokoly

Pracovní postup, který určí hlavní příčinu chyby, se liší v závislosti na typu chyby a jeho závažnosti.

### <a name="error-classification"></a>Klasifikace chyb

Na základě protokolů jsou chyby klasifikovány a počítány, aby bylo možné určit prioritu jejich šetření. Můžeme například zjistit, že "System.IO. \_ _Error. WinIOError "na" System.IO.FileStream.Init "nastala 500 časů ve verzi \<x> produktu a má nejvyšší četnost výskytů v této verzi.

### <a name="work-items-for-tracking"></a>Pracovní položky pro sledování

Pracovní položky pro jednotlivé a prioritní chyby se vytvářejí a přiřazují technikům k šetření. Tyto pracovní položky obvykle obsahují klasifikaci, prioritu a diagnostické informace, které jsou relevantní pro typ chyby. Tyto informace jsou odvozeny z shromážděných protokolů vygenerovaných systémem pro chybu. Například pracovní položka pro selhání může obsahovat trasování zásobníku, ve kterém došlo k chybě.

### <a name="error-investigation"></a>Chyba při šetření

Technici využívají informace, které jsou k dispozici v pracovní položce k určení hlavní příčiny chyby. V některých případech potřebují více informací, než jaké jsou přítomny v pracovní položce. v takovém případě odkazují na původní shromažďovaný protokol generovaný systémem. Pracovník může například zkontrolovat výpis paměti a pochopit tak selhání produktu.

## <a name="tips-for-extension-authors"></a>Tipy pro autory rozšíření

Autoři rozšíření by měli omezit expozici osobních údajů tím, že nepoužívají osobní nebo jiné citlivé informace v názvech jejich modulů, typů a metod. Pokud se v tomto kódu v zásobníku vyskytne chybový nebo podobný chybový stav, shromažďují se tyto informace jako součást protokolů generovaných systémem.

## <a name="opt-out-of-data-collection"></a>Odhlásit se od shromažďování dat

S ohledem na účel shromažďovaných dat a omezení přístupu a uchování doporučujeme použít výchozí nastavení ochrany osobních údajů pro sadu Visual Studio a Windows. Můžete se ale odhlásit [od program Zlepšování sady Visual Studio na základě zkušeností uživatelů](../ide/visual-studio-experience-improvement-program.md#opt-in-or-out) . Pokud chcete odhlásit vygenerované systémové shromažďování protokolů pro všechny programy, přečtěte si téma [Diagnostika, zpětná vazba a ochrana osobních údajů ve Windows 10](https://privacy.microsoft.com/windows-10-feedback-diagnostics-and-privacy). Možnosti se můžou lišit v závislosti na verzi systému Windows, kterou používáte.

## <a name="see-also"></a>Viz také

- [Program Zlepšování softwaru a služeb na základě zkušeností uživatelů](visual-studio-experience-improvement-program.md)
- [Diagnostika, zpětná vazba a ochrana osobních údajů ve Windows 10](https://privacy.microsoft.com/windows-10-feedback-diagnostics-and-privacy)