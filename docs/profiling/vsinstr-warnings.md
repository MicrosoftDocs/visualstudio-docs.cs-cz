---
title: Upozornění VSInstr | Microsoft Docs
ms.date: 11/04/2016
description: Přečtěte si informace o upozorněních vydaných nástrojem VSInstr.exe a o tom, jak můžete použít možnost neupozorňovat spolu s čísly upozornění k potlačení zobrazení upozornění.
ms.topic: reference
helpviewer_keywords:
- instrumentation, VSInstr tool
- warnings
- VSInstr tool
- warnings, VSInstr tool
- performance tools, VSInstr tool
ms.assetid: 47512bc9-a8e9-4628-883a-d9888edab786
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: d5510c475ab566e65d2bd152136535fde62f257b
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2021
ms.locfileid: "98723124"
---
# <a name="vsinstr-warnings"></a>Upozornění VSInstr
V následující tabulce jsou uvedena upozornění vydaná nástrojem *VSInstr.exe* . Pomocí možnosti neupozorňovat spolu s čísly upozornění můžete potlačit zobrazování upozornění.

|Číslo upozornění|Popis|
|--------------------|-----------------|
|**VSP1026**|Pokrytí není podporováno u knihoven, které neodkazují na MSCorLib. To je často případ pro přenosné knihovny.<br /><br />Možnost příkazového řádku [/EnableCodeCoverage](../test/vstest-console-options.md) se vyžaduje pro .NET Core.|
|**VSP2000**|Vnitřní chyba Nelze získat název souboru modulu pro tento spustitelný soubor.|
|**VSP2001**|\<assembly name> je silně pojmenované sestavení. Předtím, než bude možné provést zpracování, je nutné ho znovu podepsat.<br /><br /> K tomuto upozornění dochází, je-li instrumentované sestavení instrumentované. Můžete použít nástroj *sn.exe* pro opětovné podepsání binárního souboru nebo k dočasnému vypnutí požadavku silného názvu. Další informace najdete v tématu [Sn.exe (Nástroj pro silný název)](/dotnet/framework/tools/sn-exe-strong-name-tool).|
|**VSP2002**|V souboru se nenašla funkce. \<funcname>\<filename><br /><br /> K tomuto upozornění dochází, pokud funkce nemůže být umístěna v zadaném souboru.|
|**VSP2003**|V souboru nelze nalézt žádné přeskakování pro funkci \<funcname> \<filename> .<br /><br /> K tomuto upozornění dochází, pokud VSInstr nemůže nezruší průřezy. Pro optimalizaci kódu se používají různé přeskakování.|
|**VSP2004**|Funkce \<funcname> byla vyloučena pomocí přepínače příkazového řádku Exclude, ale byla požadována, protože obsahovala křížové skoky.<br /><br /> K tomuto upozornění dochází, pokud byla funkce vyloučena pomocí možnosti vyloučit, ale je nutná během procesu instrumentace. Profiler automaticky obsahuje požadovanou funkci.|
|**VSP2005**|Vnitřní chyba instrumentace \<error text><br /><br /> Toto upozornění je vydáno, pokud instrumentaci nelze provést. Zkontrolujte text chyby a určete, zda může být opraven.|
|**VSP2006**|Nelze najít soubor PDB pro \<name><br /><br /> K tomuto upozornění dochází, pokud soubor PDB v cestě pro hledání neexistuje nebo se neshoduje s binárním souborem.|
|**VSP2007**|\<filename> neobsahuje žádný instrumentující kód.<br /><br /> Toto upozornění se vydá, pokud jsou všechny funkce v binárním souboru vyloučené nebo pokud zadaný soubor obsahuje pouze prostředky.|
|**VSP2008**|Nelze získat atributy zabezpečení z \<name> . Kód chyby \<code><br /><br /> K tomuto upozornění dochází, pokud uživatel nemá oprávnění READ_DAC. Během procesu instrumentace se Profiler pokusí zachovat původní seznam DACL pro binární soubor. Vzhledem k tomu, že je původní binární soubor nahrazen novým binárním souborem, je nutné zkopírovat seznam DACL z původního binárního souboru a použít ho na nový binární soubor. To může selhat, pokud uživatel nemá READ_DAC přístup k původnímu binárnímu souboru.|
|**VSP2009**|Nelze nastavit atributy zabezpečení pro \<name> . Kód chyby \<error number><br /><br /> K tomuto upozornění dochází, pokud uživatel nemá oprávnění WRITE_DAC. Během procesu instrumentace se Profiler pokusí zachovat původní seznam DACL pro binární soubor. Vzhledem k tomu, že je původní binární soubor nahrazen novým binárním souborem, je nutné zkopírovat seznam DACL z původního binárního souboru a použít ho na nový binární soubor. To může selhat, pokud uživatel nemá WRITE_DAC přístup k novému binárnímu souboru.|
|**VSP2010**|Pro instrumentaci se konkrétně neberou žádné funkce, protože možnosti-INCLUDE/-EXCLUDE nejsou k dispozici.|
|**VSP2011**|Include/Exclude funcspec \<name> se neshodují s žádnými funkcemi.|
|**VSP2012**|Obrázek neobsahuje žádný kód, který by bylo možné instrumentovat pro pokrytí kódu.<br /><br /> Profiler neinstrumentuje následující typ kódu:<br /><br /> – Statické funkce CRT<br />-Spravované metody s atributem NonUserCodeAttribute<br />-Spravované metody s atributem DebuggerHiddenAttribute neovlivňuje<br />– Bloky MASM<br /><br /> Toto upozornění je generováno, pokud po tomto filtrování není ponechán žádný kód.|
|**VSP2013**|Instrumentace této image vyžaduje, aby běžela jako 32 proces. Příznaky hlavičky CLR byly aktualizovány tak, aby odrážely tuto skutečnost.<br /><br /> Profiler změní binární soubor tak, aby 64 operační systémy mohli otevřít 32 proces v emulátoru WOW64. V případě knihoven (DLL) to může selhat, pokud jsou načteny do existujícího 64 procesu. Toto upozornění upozorňuje uživatele na závislost.|
|**VSP2014**|Výsledný instrumentující obrázek je pravděpodobně neplatný a nemusí být spuštěn.<br /><br /> Tato zpráva se zobrazí, když má konečné instrumentované sestavení neplatnou hlavičku PE.|

## <a name="see-also"></a>Viz také
- [VSInstr](../profiling/vsinstr.md)
