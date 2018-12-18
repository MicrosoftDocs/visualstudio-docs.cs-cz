---
title: Upozornění VSInstr | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a306276e015d06fe3becf297d0bb5834f640a1a7
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2018
ms.locfileid: "34571643"
---
# <a name="vsinstr-warnings"></a>Upozornění VSInstr
Následující tabulka uvádí upozornění vydaný *VSInstr.exe* nástroj. NOWARN možnost společně s čísla upozornění můžete potlačit zobrazení této výstrahy.  
  
|Počet upozornění|Popis|  
|--------------------|-----------------|  
|**VSP2000**|Vnitřní chyba Nelze získat název souboru modulu pro tento spustitelný soubor.|  
|**VSP2001**|\<název sestavení > je silně pojmenované sestavení. Musí být znovu podepisovat, aby bylo možné spustit.<br /><br /> Toto upozornění se zobrazí, když je instrumentovány podepsané sestavení. Můžete použít *sn.exe* nástroj vzdát binárního souboru nebo zrušte zaškrtnutí políčka požadavek na silné jméno. Další informace najdete v tématu [Sn.exe (nástroj pro silný název)](/dotnet/framework/tools/sn-exe-strong-name-tool).|  
|**VSP2002**|Nepovedlo se najít funkci \<%{FuncName/ > v souboru \<název souboru ><br /><br /> Toto upozornění se zobrazí, pokud funkci nelze umístit do zadaného souboru.|  
|**VSP2003**|Nelze najít žádné křížové přeskočí funkce \<%{FuncName/ > v souboru \<název souboru >.<br /><br /> Toto upozornění se zobrazí pokud vsinstr – nelze nezruší se tím přejde mezi. Optimalizace kódu se používají křížové přeskočí.|  
|**VSP2004**|Funkce \<%{FuncName/ > vyloučil pomocí přepínače příkazového řádku vyloučení, ale nebyla nutná, protože v něm křížové přechod.<br /><br /> Toto upozornění se zobrazí, pokud funkce se vyloučila pomocí možnosti vyloučení, ale je potřeba během procesu instrumentace. Profileru automaticky zahrne požadované funkce.|  
|**VSP2005**|Vnitřní chyba instrumentace \<text chyby ><br /><br /> Pokud není možné instrumentace se objeví toto upozornění. Zkontrolujte text chyby k určení, zda může být vyřešen.|  
|**VSP2006**|Nelze najít PDB pro \<name ><br /><br /> Toto upozornění se zobrazí, pokud je soubor PDB na cesta hledání neexistuje nebo neodpovídá binárního souboru.|  
|**VSP2007**|\<Název souboru > neobsahuje žádný instrumentable kód.<br /><br /> Pokud funkce v binárním souboru všechny vyloučené nebo pokud je zadaný soubor obsahuje pouze prostředky se objeví toto upozornění.|  
|**VSP2008**|Nelze získat atributy zabezpečení z \<name >. Kód chyby \<kód ><br /><br /> Toto upozornění se zobrazí, pokud uživatel nemá oprávnění READ_DAC. Během procesu instrumentace profileru snaží se zachovat původní seznam DACL pro binárního souboru. Vzhledem k tomu, že původní binárního souboru se nahradí nové binární, musí být seznam DACL z původní binárního souboru zkopírovat a použít pro nové binárního souboru. To může selhat, pokud uživatel nemá přístup READ_DAC na původní binárního souboru.|  
|**VSP2009**|Nelze nastavit atributy zabezpečení u \<name >. Kód chyby \<číslo chyby ><br /><br /> Toto upozornění se zobrazí, pokud uživatel nemá oprávnění zápis_DAC. Během procesu instrumentace profileru snaží se zachovat původní seznam DACL pro binárního souboru. Vzhledem k tomu, že původní binárního souboru se nahradí nové binární, musí být seznam DACL z původní binárního souboru zkopírovat a použít pro nové binárního souboru. To může selhat, pokud uživatel nemá přístup zápis_DAC na nové binárního souboru.|  
|**VSP2010**|Konkrétně se žádná funkce vybrané pro instrumentace z důvodu - ZAHRNOVAT možnosti/vyloučení|  
|**VSP2011**|Zahrnutí a vyloučení funcspec \<name > neodpovídá žádné funkce.|  
|**VSP2012**|Obrázek neobsahuje kód, který může být instrumentována pro pokrytí kódu.<br /><br /> Profileru není instrumentace následující typ kódu:<br /><br /> -Statický CRT – funkce<br />-Spravované metody opatřená NonUserCodeAttribute<br />-Spravované metody opatřená DebuggerHiddenAttribute<br />– MASM bloky<br /><br /> Toto upozornění je generováno Pokud po tomto filtrování se není žádný kód vlevo.|  
|**VSP2013**|Instrumentace tuto bitovou kopii vyžaduje, aby spustit jako 32bitový proces. Příznaky hlavičky CLR byly aktualizovány tak, aby odrážela to.<br /><br /> Profileru upravuje binárního souboru tak, aby 64bitové operační systémy v emulátoru WOW64 můžete otevřít 32bitový proces. Pro knihovny (DLL) to může selhat, pokud jsou načteny v existující 64bitového procesu. Toto upozornění upozorní uživatele závislosti.|  
|**VSP2014**|Výsledný instrumentovaného bitové kopie pravděpodobně není platný a nemusí být možné spustit.<br /><br /> Tato zpráva se zobrazí při posledním instrumentovaného sestavení má neplatnou hlavičku PE.|  
  
## <a name="see-also"></a>Viz také:  
 [VSInstr](../profiling/vsinstr.md)