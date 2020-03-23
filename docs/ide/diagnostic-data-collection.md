---
title: Diagnostická data a protokoly generované systémem
ms.date: 05/24/2018
ms.topic: conceptual
author: jillre
ms.author: michma
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9702439569fa9db1ff8687e914d5c9d20865e2b0
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "72652465"
---
# <a name="system-generated-logs-collected-by-visual-studio"></a>Protokoly generované systémem shromážděné souborem Visual Studio

Visual Studio shromažďuje protokoly generované systémem k opravě problémů a zlepšení kvality produktu prostřednictvím [programu Visual Studio Customer Experience Improvement Program](visual-studio-experience-improvement-program.md). Tento článek obsahuje některé informace o typech dat, které shromažďujeme, a o tom, jak je používáme. Poskytuje také tipy, jak se autoři rozšíření mohou vyhnout neúmyslnému zveřejnění osobních nebo citlivých informací.

## <a name="types-of-collected-data"></a>Typy shromážděných údajů

Visual Studio shromažďuje protokoly generované systémem pro selhání, zablokování, nereagující uživatelské rozhraní a vysoké využití procesoru nebo paměti. Shromažďujeme také informace o chybách, ke kterým došlo při instalaci nebo používání produktu. Shromážděná data se liší v závislosti na chybě a mohou zahrnovat trasování zásobníku, výpisy stavu paměti a informace o výjimce:

- Pro vysoké využití procesoru a neodpovídá, zásobníktrasy příslušných podprocesů sady Visual Studio jsou shromažďovány.

- V případech, kdy trasování zásobníku některých vláken nestačí k určení hlavní příčiny problému, například selhání, zablokování nebo vysoké využití paměti, shromažďujeme *výpis*stavu paměti . Výpis představuje stav procesu, kdy došlo k chybě.

- Pro neočekávané chybové stavy, například výjimku při pokusu o zápis do souboru na disku, shromažďujeme informace o výjimce. Informace zahrnují název výjimky, trasování zásobníku vlákna, kde došlo k výjimce, zprávu přidruženou k výjimce a další informace týkající se konkrétní výjimky.

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

## <a name="how-we-use-system-generated-logs"></a>Jak používáme protokoly generované systémem

Pracovní postup k určení hlavní příčiny chyby se liší v závislosti na typu chyby a její závažnosti.

### <a name="error-classification"></a>Klasifikace chyb

Na základě protokolů jsou chyby klasifikovány a počítány tak, aby upřednostňovaly jejich vyšetřování. Například můžeme zjistit, že "System.IO. \__Error.WinIOError" na "System.IO.FileStream.Init" došlo 500 \<krát ve verzi x> produktu a má nejvyšší rychlost výskytu v této verzi.

### <a name="work-items-for-tracking"></a>Pracovní položky pro sledování

Pracovní položky pro jednotlivé chyby s prioritou jsou vytvořeny a přiřazeny technikům k šetření. Tyto pracovní položky obvykle obsahují informace o klasifikaci, prioritě a diagnostice týkající se typu chyby. Tyto informace jsou odvozeny ze shromážděných protokolů generovaných systémem pro chybu. Například pracovní položka pro selhání může obsahovat trasování zásobníku, kde dochází k chybě.

### <a name="error-investigation"></a>Šetření chyb

Inženýři použít informace, které jsou k dispozici v pracovní položce k určení hlavní příčinu chyby. V některých případech potřebují více informací než co je k dispozici v pracovní položce, v takovém případě odkazují na původní protokol generovaný systémem, který byl shromážděn. Například technik může zkontrolovat výpis stavu paměti pochopit selhání produktu.

## <a name="tips-for-extension-authors"></a>Tipy pro autory rozšíření

Autoři rozšíření by měli omezit expozici osobních informací tím, že nebudou používat osobní nebo jiné citlivé informace v názvech svých modulů, typů a metod. Pokud dojde k selhání nebo podobné chybové podmínky s tímto kódem v zásobníku, tyto informace získá shromážděny jako součást protokoly generované systémem.

## <a name="opt-out-of-data-collection"></a>Odhlásit se ze shromažďování údajů

Vzhledem k účelu shromažďovacích údajů a omezením jejich přístupu a uchovávání doporučujeme použít výchozí nastavení ochrany osobních údajů pro sady Visual Studio a systém Windows. Můžete se však [odhlásit](../ide/visual-studio-experience-improvement-program.md#opt-in-or-out) z programu Visual Studio Experience Improvement Program. Pokud se chcete odhlásit ze systémově generované kolekce protokolů pro všechny programy, přečtěte si část [Diagnostika, zpětná vazba a ochrana osobních údajů ve Windows 10](https://privacy.microsoft.com/windows-10-feedback-diagnostics-and-privacy). Možnosti se mohou lišit v závislosti na verzi systému Windows, kterou používáte.

## <a name="see-also"></a>Viz také

- [Program Zlepšování softwaru a služeb na základě zkušeností uživatelů pro Visual Studio](visual-studio-experience-improvement-program.md)
- [Diagnostika, zpětná vazba a ochrana osobních údajů ve Windows 10](https://privacy.microsoft.com/windows-10-feedback-diagnostics-and-privacy)