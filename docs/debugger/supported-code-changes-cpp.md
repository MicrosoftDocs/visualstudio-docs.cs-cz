---
title: Podporované změny kódu (C++) | Microsoft Docs
description: Informace o tom, jaké změny kódu jsou podporovány při použití funkce upravit a pokračovat při ladění projektu C++ v aplikaci Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/18/2020
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Edit and Continue, limitations
- supported code changes
- object files, limitations of Edit and Continue
- C++ language, supported code changes
- coding, supported code changes
- resource files, limitations of Edit and Continue
- code changes, handling in Edit and Continue
- what's new [C++], supported code changes
- code changes
ms.assetid: f5754363-8a56-417b-b904-b05d9dd26d03
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: d693753cbcc9844ff602ab4d20e90fdc6de7dae5
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/13/2021
ms.locfileid: "98150493"
---
# <a name="supported-code-changes-c"></a>Podporované změny kódu (C++)
Upravit a pokračovat pro projekty v jazyce C++ zpracovává většinu typů změn kódu. V průběhu provádění programu však nelze některé změny použít. Chcete-li tyto změny použít, je nutné zastavit provádění a vytvořit novou verzi kódu.

 Informace o práci s úpravou a pokračováním pro jazyk C++ v aplikaci Visual Studio naleznete v tématu [Upravit a pokračovat (C++)](../debugger/edit-and-continue-visual-cpp.md) .

## <a name="requirements"></a><a name="BKMK_Requirements"></a> Požadavků
### <a name="build-settings-project--properties"></a>Nastavení sestavení (vlastnosti projektu >):
  1. **C/C++ > Obecné informace o ladění > formátu**: databáze programu pro upravit a pokračovat ( `/ZI` )
  2. **C/C++ > generování kódu > povolení minimálního opětovného sestavení**: Ano ( `/Gm` )
  3. **Linker > obecné > povolení přírůstkového propojení**: Ano ( `/INCREMENTAL` )

     Všechna nekompatibilní nastavení linkeru (například `/SAFESEH` nebo `/OPT:` ...) by měla při sestavování způsobit upozornění _linkerů LNK4075_ .  
     Příklad: `LINK : warning LNK4075: ignoring '/INCREMENTAL' due to '/OPT:ICF' specification`

### <a name="debugger-settings-debug--options--general"></a>Nastavení ladicího programu (možnosti ladění > > Obecné):
  - Povolit nativní úpravu a pokračování

     Při úpravách a pokračování způsobuje jakákoli nekompatibilní nastavení kompilátoru nebo linkeru chybu.  
     Příklad: `Edit and Continue : error  : ‘file.cpp’ in ‘MyApp.exe’ was not compiled with Edit and Continue enabled. Ensure that the file is compiled with the Program Database for Edit and Continue (/ZI) option.`

## <a name="unsupported-changes"></a><a name="BKMK_Unsupported_changes"></a> Nepodporované změny
 Následující změny jazyka C/C++ nelze použít během relace ladění. Pokud provedete některé z těchto změn a pokusíte se použít změny kódu, zobrazí se v okně **výstup** chybová zpráva nebo upozornění.

- Většina změn globálních nebo statických dat.

- Změny spustitelných souborů, které jsou zkopírovány z jiného počítače a nejsou vytvořeny místně.

- Změny datového typu, které ovlivňují rozložení objektu, například datových členů třídy.

- Přidání více než 64kb bajtů nového kódu nebo dat.

- Přidání proměnných, které vyžadují konstruktor v bodě před ukazatelem na instrukci.

- Změny ovlivňující kód, který vyžaduje inicializaci za běhu.

- Přidání obslužných rutin výjimek, v některých případech.

- Změny souborů prostředků.

- Změny kódu v souborech jen pro čtení.

- Změny kódu bez odpovídajícího souboru PDB.

- Změny kódu, který nemá žádný soubor objektu.

* Úpravy výrazů lambda:
  - Mít statický nebo globální člen.
  - Jsou předány do funkce std:: Function. To způsobí porušení originálního ODR a výsledků C1092.

- Upravit a pokračovat neprovede aktualizace statických knihoven. Pokud provedete změnu ve statické knihovně, vykonání pokračuje ve staré verzi a nebude vydáno žádné upozornění.

## <a name="unsupported-scenarios"></a><a name="BKMK_Unsupported_scenarios"></a> Nepodporované scénáře
 Úpravy a pokračování pro C/C++ nejsou k dispozici v následujících scénářích ladění:

- Ladění nativních aplikací kompilovaných pomocí [/Zo (rozšířené optimalizované ladění)](/cpp/build/reference/zo-enhance-optimized-debugging)

- Ve verzích sady Visual Studio předcházejících aktualizaci Visual Studio 2015 Update 1 ladí aplikace nebo komponenty UWP. Počínaje verzí Visual Studio 2015 Update 1 můžete použít příkaz Upravit a pokračovat v aplikacích pro UWP C++ a aplikacích rozhraní DirectX, protože teď podporuje `/ZI` přepínač kompilátoru s  `/bigobj` přepínačem. V případě binárních souborů kompilovaných s přepínačem můžete také použít možnost upravit a pokračovat `/FASTLINK` .

- Ladění aplikací ze Storu 8/8.1 Tyto projekty používají sadu nástrojů VC 120 a přepínač jazyka C/C++ `/bigobj` . Úpravy a pokračování v nástroji `/bigobj` se podporují jenom v sadě nástrojů VC 140.

- Ladění ve Windows 98.

- Ladění ve smíšeném režimu (nativní/spravované)

- Ladění JavaScriptu.

- Ladění SQL.

- Ladění souboru s výpisem paměti.

- Úprava kódu po neošetřené výjimce, pokud není vybrána možnost **unwind zásobníku volání při neošetřených výjimkách** .

- Ladění aplikace pomocí možnosti **připojit** místo spuštění aplikace, a to tak, že v nabídce **ladění** kliknete na možnost **Spustit** .

- Ladění optimalizovaného kódu.

- Ladění staré verze kódu po neúspěšném sestavení nové verze z důvodu chyb sestavení.

- Použití vlastní cesty kompilátoru (*cl.exe*). Z bezpečnostních důvodů, pro rekompilaci souboru během úprav a pokračování, Visual Studio vždy používá instalovaný kompilátor. Pokud používáte vlastní cestu kompilátoru (například prostřednictvím vlastní `$(ExecutablePath)` proměnné v `*.props` souboru), zobrazí se upozornění a Visual Studio se vrátí k použití nainstalovaného kompilátoru stejné verze nebo architektury.

- FASTBuild sestavovací systém. FASTBuild není aktuálně kompatibilní s přepínačem Enable minimálního opětovného sestavení ( `/Gm` ), takže možnost upravit a pokračovat není podporována.

- Starší verze architektury/sady nástrojů VC. Pomocí sady nástrojů VC 140 podporuje výchozí ladicí program úpravy a pokračování v aplikacích pro x86 i x64. Starší sady nástrojů podporují pouze aplikace x86. Sady nástrojů starší než VC 120 by měly používat starší verzi ladicího programu, a to zaškrtnutím _možnosti ladění > > obecné >_ použít nativní režim kompatibility, aby bylo možné použít příkaz Upravit a pokračovat.

## <a name="linking-limitations"></a><a name="BKMK_Linking_limitations"></a> Omezení propojení

### <a name="linker-options-that-disable-edit-and-continue"></a><a name="BKMK_Linker_options_that_disable_Edit_and_Continue"></a> Možnosti linkeru, které zakazují úpravu a pokračování
 Následující možnosti linkeru zakazují možnost upravit a pokračovat:

- Nastavení **/OPT: ref**, **/OPT: ICF** nebo **/incremental: žádné** zakáže příkaz Upravit a pokračovat s následujícím upozorněním:  
     `LINK : warning LNK4075: ignoring /EDITANDCONTINUE due to /OPT specification`

- Nastavení **/Order**, **/release** nebo **/Force** zakáže příkaz Upravit a pokračovat s následujícím upozorněním:  
     `LINK : warning LNK4075: ignoring /INCREMENTAL due to /option specification`

- Nastavení jakékoli možnosti, která znemožňuje vytvoření souboru databáze programu (PDB), zakáže příkaz Upravit a pokračovat bez konkrétního upozornění.

### <a name="auto-relinking-limitations"></a><a name="BKMK_Auto_relinking_limitations"></a> Omezení automatického přepojování
 Ve výchozím nastavení příkaz Upravit a pokračovat znovu propojí na konci relace ladění a vytvoří aktuální spustitelný soubor.

 Upravit a pokračovat nemůže znovu propojit program, pokud ho ladíte z jiného umístění, než je původní umístění sestavení. Zobrazí se zpráva s informacemi o tom, že je potřeba znovu sestavit ručně.

 Při úpravě a pokračování nedojde k opakovanému sestavování statických knihoven. Pokud provedete změny statické knihovny pomocí upravit a pokračovat, budete muset ručně znovu sestavit knihovnu a znovu propojit aplikace, které ji používají.

 Funkce Upravit a pokračovat nevyvolává vlastní kroky sestavení. Pokud program používá vlastní kroky sestavení, je nutné provést ruční opětovné sestavení, aby se vyvolaly vlastní kroky sestavení. V tom případě je možné vypnout propojování po funkci Upravit a pokračovat, aby bylo zaručeno, že budete vyzváni, abyste provedli ruční znovu sestavení.

 **Zakázání přepojování po úpravě a pokračování**

1. V nabídce **ladění** vyberte **Možnosti a nastavení**.

2. V dialogovém okně **Možnosti** pod uzlem **ladění** a vyberte uzel **Upravit a pokračovat** .

3. Zrušte zaškrtnutí políčka **znovu propojit změny kódu po ladění** .

## <a name="precompiled-header-limitations"></a><a name="BKMK_Precompiled_header_limitations"></a> Omezení předkompilované hlavičky
 Ve výchozím nastavení se při úpravách a pokračování načte a zpracovává předkompilovaných hlaviček na pozadí, aby se urychlilo zpracování změn kódu. Načtení předkompilovaných hlaviček vyžaduje přidělení fyzické paměti, což může být problém, pokud kompilujete na počítači s omezeným pamětí RAM. Můžete určit, zda se jedná o problém pomocí Správce úloh systému Windows k určení množství dostupné fyzické paměti při ladění. Pokud je tato hodnota vyšší než velikost předkompilovaných hlaviček, pak by funkce Upravit a pokračovat neměla mít problém. Pokud je velikost menší než velikost předkompilovaných hlaviček, můžete zabránit možnostem upravit a pokračovat v načítání předkompilovaných hlaviček na pozadí.

 **Zakázání načítání předkompilovaných hlaviček na pozadí pro úpravy a pokračování**

1. V nabídce **ladění** vyberte **Možnosti a nastavení**.

2. V dialogovém okně **Možnosti** pod uzlem **ladění** a vyberte uzel **Upravit a pokračovat** .

3. Zrušte zaškrtnutí políčka **Povol předkompilování** .

## <a name="idl-attribute-limitations"></a><a name="BKMK_IDL_attribute_limitations"></a> Omezení atributů IDL
 Upravit a pokračovat negeneruje znovu negenerované soubory definice rozhraní (IDL). Proto se změny atributů IDL nebudou odrazit při ladění. Chcete-li zobrazit výsledek změn atributů IDL, je nutné zastavit ladění a znovu sestavit aplikaci. Upravit a pokračovat negeneruje chybu nebo upozornění, pokud se změnily atributy IDL. Další informace naleznete v tématu [IDL – atributy](/cpp/windows/idl-attributes).

## <a name="diagnosing-issues"></a><a name="BKMK_Diagnosing_issues"></a> Diagnostikování problémů
 Pokud váš scénář nevyhovuje žádné z výše uvedených podmínek, můžete získat další podrobnosti nastavením následující hodnoty registru typu DWORD:
 1. Otevřete Developer Command Prompt.
 2. Spusťte následující příkaz:  
     `VsRegEdit.exe set “C:\Program Files (x86)\Microsoft Visual Studio\[Version]\[YOUR EDITION]” HKCU Debugger NativeEncDiagnosticLoggingLevel DWORD 1`

 Nastavením této hodnoty na začátku relace ladění dojde k tomu, že různé součásti příkazu Upravit a pokračovat Spew podrobné protokolování do   >  podokna **ladění** okno výstup.

## <a name="see-also"></a>Viz také
- [Upravit a pokračovat (C++)](../debugger/edit-and-continue-visual-cpp.md)
