---
title: VSInstr Varování | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: f1a0cba29caeda01de1154430af7a0d94bcfc2a5
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779945"
---
# <a name="vsinstr-warnings"></a>VSInstr varování
V následující tabulce jsou uvedena upozornění vydaná nástrojem *VSInstr.exe.* Možnost NOWARN spolu s výstražnými čísly můžete použít k potlačení zobrazení upozornění.

|Číslo upozornění|Popis|
|--------------------|-----------------|
|**VSP1026**|Pokrytí není podporováno v knihovnách, které neodkazují na MSCorLib. To je často případ přenosných knihoven.<br /><br />Možnost příkazového řádku [/EnableCodeCoverage](../test/vstest-console-options.md) je vyžadována pro jádro .NET Core.|
|**VSP2000**|Vnitřní chyba Pro tento spustitelný soubor nelze získat název souboru modulu.|
|**VSP2001**|\<název sestavení> je silně pojmenované sestavení. Před spuštěním musí být znovu podepsán.<br /><br /> K tomuto upozornění dochází, když je podepsané sestavení instrumentované. Pomocí nástroje *sn.exe* můžete odstoupit od binárního souboru nebo dočasně vypnout požadavek na silný název. Další informace naleznete v [tématu Sn.exe (nástroj se silným názvem).](/dotnet/framework/tools/sn-exe-strong-name-tool)|
|**VSP2002**|V> \<názvu souboru \<nelze najít funkci funcname><br /><br /> K tomuto upozornění dochází, pokud funkci nelze nalézt v zadaném souboru.|
|**VSP2003**|V názvu souboru \< \<> nelze najít žádné křížové skoky na funkci funcname>.<br /><br /> K tomuto upozornění dochází, pokud VSInstr nelze zrušit křížové skoky. Křížové skoky se používají pro optimalizaci kódu.|
|**VSP2004**|Funkce \<funcname> byla vyloučena pomocí přepínače příkazového řádku EXCLUDE, ale byla vyžadována, protože obsahovala křížový skok.<br /><br /> K tomuto upozornění dochází, pokud byla funkce vyloučena pomocí možnosti EXCLUDE, ale je potřeba během procesu instrumentace. Profiler automaticky obsahuje požadovanou funkci.|
|**VSP2005**|Text chyby \<vnitřní instrumentace><br /><br /> Toto upozornění se vydává, pokud nelze provést instrumentaci. Zkontrolujte text chyby a zjistěte, zda jej lze opravit.|
|**VSP2006**|Nelze najít pdb \<pro název><br /><br /> K tomuto upozornění dochází, pokud soubor PDB neexistuje v cestě hledání nebo neodpovídá binárnímu souboru.|
|**VSP2007**|\<název souboru> neobsahuje žádný instrumentovatelný kód.<br /><br /> Toto upozornění je vydáno, pokud byly všechny funkce v binárním souboru vyloučeny nebo pokud zadaný soubor obsahuje pouze prostředky.|
|**VSP2008**|Nelze získat atributy \<zabezpečení z> názvu. > \<kódu kódu chyby<br /><br /> K tomuto upozornění dochází, pokud uživatel nemá oprávnění READ_DAC. Během procesu instrumentace profiler pokusí zachovat původní DACL pro binární. Vzhledem k tomu, že původní binární soubor je nahrazen novým binárním souborem, musí být seznam DACL z původního binárního souboru zkopírován a použit na nový binární soubor. To může selhat, pokud uživatel nemá READ_DAC přístup k původnímu binárnímu souboru.|
|**VSP2009**|Nelze nastavit atributy \<zabezpečení pro> názvů. Číslo \<chyby kódu><br /><br /> K tomuto upozornění dochází, pokud uživatel nemá WRITE_DAC oprávnění. Během procesu instrumentace profiler pokusí zachovat původní DACL pro binární. Vzhledem k tomu, že původní binární soubor je nahrazen novým binárním souborem, musí být seznam DACL z původního binárního souboru zkopírován a použit na nový binární soubor. To může selhat, pokud uživatel nemá WRITE_DAC přístup k novému binárnímu souboru.|
|**VSP2010**|Pro instrumentaci nejsou speciálně vybrány žádné funkce z důvodu možností -INCLUDE/-EXCLUDE.|
|**VSP2011**|Zahrnout/vyloučit název \<funcspec> neodpovídá žádné funkci|
|**VSP2012**|Obrázek neobsahuje žádný kód, který může být instrumentován pro pokrytí kódu.<br /><br /> Profiler nepředstavuje tento typ kódu:<br /><br /> - Statické funkce CRT<br />- Spravované metody přiřazené s NonUserCodeAttribute<br />- Spravované metody přiřazené debuggerhiddenattribute<br />- MASM bloky<br /><br /> Toto upozornění je generováno, pokud po tomto filtrování nezbývá žádný kód.|
|**VSP2013**|Instrumentace tohoto obrázku vyžaduje, aby byl spuštěn jako 32bitový proces. Příznaky hlavičky CLR byly aktualizovány tak, aby odrážely toto.<br /><br /> Profiler upraví binární tak, aby 64bitové operační systémy můžete otevřít 32bitový proces v wow64 emulátoru. Pro knihovny (DLL) to může selhat, pokud jsou načteny v existujícím 64bitovém procesu. Toto upozornění upozorní uživatele na závislost.|
|**VSP2014**|Výsledný instrumentovaný obrázek se zdá být neplatný a nemusí být spuštěn.<br /><br /> Tato zpráva nastane, když konečné instrumentované sestavení má neplatné hlavičky PE.|

## <a name="see-also"></a>Viz také
- [VSInstr](../profiling/vsinstr.md)
