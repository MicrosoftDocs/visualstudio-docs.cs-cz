---
title: Generované systémem protokoly a diagnostických dat
ms.date: 05/24/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
author: gewarren
ms.author: michma
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f55d8a0f32886ed477026e298ed2c8c5d6e26f16
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/05/2018
ms.locfileid: "34478348"
---
# <a name="system-generated-logs-collected-by-visual-studio"></a>Shromážděné sadou Visual Studio protokoly generované systémem

Visual Studio shromažďuje protokoly generovaný systémem a opravte problémy, ke zvyšování kvality produktu pomocí [programu zlepšování zkušeností zákazníků sady Visual Studio](visual-studio-experience-improvement-program.md). Tento článek obsahuje některé informace o typech dat, které shromažďujeme a způsob jejich použití. Poskytuje také tipy, jak autorům rozšíření se můžete vyhnout náhodné zveřejnění osobních nebo citlivých informací.

## <a name="types-of-collected-data"></a>Typy shromažďovaných dat

Visual Studio shromažďuje protokoly generované systémem dojde k chybě, zablokuje, absence reagování uživatelského rozhraní a vysoké využití procesoru nebo paměti. Můžeme také shromažďovat informace o chyb zjištěných při instalaci produktu nebo využití. Shromážděná data se liší podle chyba a můžou obsahovat informace o výjimce, trasování zásobníku a výpisy paměti:

- Pro vysoké využití procesoru a absence reagování se shromažďují trasování zásobníku relevantní vláken v sadě Visual Studio.

- Pro případy, kdy trasování zásobníku některé vláken nejsou dost k určení kořenové způsobit problému, například dojde k chybě, zablokování nebo využití velkého množství paměti, shromažďujeme paměti *výpis*. Výpis představuje stav procesu, když došlo k chybě.

- Došlo k neočekávané chybě podmínky, například výjimku při pokusu o zápis do souboru na disku, můžeme shromažďovat informace o výjimce. Informace zahrnují název výjimku, trasování zásobníku pro vlákno, ve kterém k výjimce došlo, zpráva přidružená výjimku a další informace, které jsou relevantní pro konkrétní výjimky.

   Shromážděná data na následující příklad ukazuje název výjimky, trasování zásobníku a zpráva o výjimce:

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

## <a name="how-we-use-system-generated-logs"></a>Jak používáme generována protokoly

Postup určení kořenové příčiny chyby se liší v závislosti na typu chyby a jeho závažnosti.

### <a name="error-classification"></a>Chyba klasifikace

Podle toho, protokoly, jsou chyby klasifikované a počítají k určení priority jejich šetření. Například může zjistíme, že "System.IO. \__Error.WinIOError "na"System.IO.FileStream.Init"došlo k 500 časy ve verzi \<x > produktu, a má nejvyšší počet výskyt v této verzi.

### <a name="work-items-for-tracking"></a>Pro sledování pracovních položek

Pracovní položky pro jednotlivé, seřazený podle priority chyby se vytváří a přiřazené technikům pro šetření. Tyto pracovní položky obvykle obsahují klasifikace, prioritu a diagnostické informace, které jsou relevantní pro typ chyby. Tyto informace je odvozená od shromažďovat protokoly generována chyba. Pracovní položku pro havárie může například obsahovat trasování zásobníku, kde dochází k havárii.

### <a name="error-investigation"></a>Chyba šetření

Technici použijte informace k dispozici v pracovní položce určit hlavní příčinu chyby. V některých případech potřebují další informace, než se nachází v rámci pracovní položky v takovém případě se naleznete v původní protokolu generované systémem, která nebyla shromážděna. Technika může například zkontrolovat výpis stavu paměti pochopit havárie produktu.

## <a name="tips-for-extension-authors"></a>Tipy pro autory rozšíření

Autoři rozšíření měli omezit expozice osobní údaje bez použití osobních nebo jinými důvěrnými informacemi v názvech jejich modulů, typy a metody. Pokud pomocí tohoto kódu v zásobníku dojde k chybě nebo podobné chybový stav, tyto informace získá shromažďuje jako součást protokoly generované systémem.

## <a name="opt-out-of-data-collection"></a>Vyjádření výslovného nesouhlasu s shromažďování dat

Zadaný účel data, která shromažďujeme a omezení u jeho přístup a uchovávání, doporučujeme, abyste použili výchozí nastavení ochrany osobních údajů pro Visual Studio a systému Windows. Můžete však [chodit](../ide/visual-studio-experience-improvement-program.md#opt-in-or-out) z programu zlepšování zkušeností Visual Studio. Pro vyjádření výslovného nesouhlasu kolekce generována protokolu pro všechny programy, najdete v části [diagnostiky, zpětnou vazbu a ochrana osobních údajů ve Windows 10](https://privacy.microsoft.com/windows-10-feedback-diagnostics-and-privacy). Možnosti se mohou lišit v závislosti na verzi Windows, který používáte.

## <a name="see-also"></a>Viz také:

- [Program Zlepšování softwaru a služeb na základě zkušeností uživatelů](visual-studio-experience-improvement-program.md)
- [Diagnostika, zpětnou vazbu a ochrana osobních údajů ve Windows 10](https://privacy.microsoft.com/windows-10-feedback-diagnostics-and-privacy)