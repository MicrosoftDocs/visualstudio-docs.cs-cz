---
title: Upozornění VSInstr | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- instrumentation, VSInstr tool
- warnings
- VSInstr tool
- warnings, VSInstr tool
- performance tools, VSInstr tool
ms.assetid: 47512bc9-a8e9-4628-883a-d9888edab786
caps.latest.revision: 25
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: be30404e4fb9cff6c53bb3afbdedb4ce03ba2d80
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51765143"
---
# <a name="vsinstr-warnings"></a>Upozornění VSInstr
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Následující tabulka obsahuje seznam upozornění vydané nástroj VSInstr.exe. Možnost NOWARN spolu s čísla upozornění můžete potlačit upozornění nezobrazovalo.  
  
|Číslo upozornění|Popis|  
|--------------------|-----------------|  
|**VSP2000**|Vnitřní chyba Nelze získat název souboru modulu tohoto spustitelného souboru.|  
|**VSP2001**|\<název sestavení > je sestavení se silným názvem. Musí být znovu podepsat předtím, než mohou být provedeny.<br /><br /> K tomuto upozornění dochází, když je instrumentováno podepsané sestavení. Binární soubor znovu podepsat nebo dočasně vypnout požadavek silným názvem, můžete použít nástroj sn.exe. Další informace najdete v tématu [Sn.exe (nástroj Strong Name)](http://msdn.microsoft.com/library/c1d2b532-1b8e-4c7a-8ac5-53b801135ec6).|  
|**VSP2002**|Nelze nalézt funkci \<funcname > v souboru \<název souboru ><br /><br /> K tomuto upozornění dochází, pokud funkci nelze umístit do zadaného souboru.|  
|**VSP2003**|Nelze nalézt žádné křížové skoky na funkci \<funcname > v souboru \<název souboru >.<br /><br /> K tomuto upozornění dochází Pokud nemůže nástroj VSInstr nezruší se tím přejde mezi. Optimalizace kódu se používají křížových skoků.|  
|**VSP2004**|Funkce \<funcname > byla vyloučena prostřednictvím přepínače příkazového řádku vyloučení, ale byla požadována, protože obsahovala křížový skok.<br /><br /> K tomuto upozornění dochází, pokud byl vyloučen, pomocí možnosti vyloučit funkce, ale je potřeba během procesu instrumentace. Profiler automaticky zahrne požadované funkce.|  
|**VSP2005**|Vnitřní chyba instrumentace \<text chyby ><br /><br /> Pokud nelze provést instrumentaci se objeví toto upozornění. Přečtěte si text chyby k určení, zda je možné odstranit.|  
|**VSP2006**|Nelze najít soubor PDB pro \<name ><br /><br /> K tomuto upozornění dochází, pokud neexistuje na cestě pro vyhledávání nebo binárním souboru neodpovídá souboru PDB.|  
|**VSP2007**|\<Název souboru > neobsahuje žádný instrumentovatelný kód.<br /><br /> Pokud funkce v binárním souboru všechny vyloučené nebo pokud zadaný soubor obsahuje pouze prostředky se objeví toto upozornění.|  
|**VSP2008**|Nepovedlo se získat atributy zabezpečení z \<název >. Kód chyby: \<kód ><br /><br /> K tomuto upozornění dochází, pokud uživatel nemá oprávnění READ_DAC. Během procesu instrumentace profileru snaží se zachovat původní seznam DACL pro binární soubor. Protože nové binární soubor nahradí původní binární soubor, musí být DACL z původní binární soubor zkopírovat a použít pro nové binární soubor. To může selhat, pokud uživatel nemá přístup READ_DAC na původní binární soubor.|  
|**VSP2009**|Nelze nastavit atributy zabezpečení na \<název >. Kód chyby: \<číslo chyby ><br /><br /> K tomuto upozornění dochází, pokud uživatel nemá oprávnění WRITE_DAC. Během procesu instrumentace profileru snaží se zachovat původní seznam DACL pro binární soubor. Protože nové binární soubor nahradí původní binární soubor, musí být DACL z původní binární soubor zkopírovat a použít pro nové binární soubor. To může selhat, pokud uživatel nemá přístup WRITE_DAC na nové binární soubor.|  
|**VSP2010**|Žádné funkce jsou speciálně vybrané pro instrumentaci z důvodu - ZAHRNUJÍ možnosti/vyloučení|  
|**VSP2011**|Zahrnutí a vyloučení funcspec \<name > neodpovídá žádné funkce|  
|**VSP2012**|Na obrázku neobsahuje žádný kód, který může být instrumentováno pro pokrytí kódu.<br /><br /> Profiler není instrumentace následující typ kódu:<br /><br /> -Statické funkce CRT<br />-Spravovaných metod s NonUserCodeAttribute<br />-Spravovaných metod DebuggerHiddenAttribute – atribut<br />– MASM bloky<br /><br /> Toto upozornění je generováno, pokud po tomto filtrování, neexistuje žádný kód vlevo.|  
|**VSP2013**|Instrumentace tohoto obrazu vyžaduje ji spustit jako 32bitový proces. Hlavičkové příznaky CLR byly aktualizovány tak, aby odrážely to.<br /><br /> Profiler upravuje binárního souboru, takže 64bitové operační systémy můžete otevřít v emulátoru WOW64 32bitový proces. Pro knihovny (DLL) to může selhat, pokud jsou načteny v existující 64bitového procesu. Toto upozornění upozorní uživatele závislosti.|  
|**VSP2014**|Výsledný instrumentovaný obraz se zdá být neplatný a nemusí být možné spustit.<br /><br /> Tato zpráva se zobrazí při posledním instrumentované sestavení má neplatná PE hlavička.|  
  
## <a name="see-also"></a>Viz také  
 [VSInstr](../profiling/vsinstr.md)



