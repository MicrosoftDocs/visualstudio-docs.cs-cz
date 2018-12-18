---
title: Ladění textové šablony T4 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- text templates, troubleshooting
- text templates, debugging
ms.assetid: 0877fdf2-20bf-42da-b3cc-4c5856b80821
caps.latest.revision: 30
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: f299b89f7f59cbfc043bb77e6e56c3e5fac22d16
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49298906"
---
# <a name="debugging-a-t4-text-template"></a>Ladění textové šablony T4
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete nastavit zarážky v textových šablonách. Chcete-li ladit návrhové textové šablony, uložte soubor textové šablony a pak zvolte **ladit šablonu T4** v místní nabídce souboru v Průzkumníku řešení. Ladění za běhu textové šablony, jednoduše ladit aplikaci, do které patří.  
  
 Ladění textové šablony, měli byste porozumět kroky transformace procesu šablony. Různé druhy chyb může dojít v rámci každého kroku. Kroky jsou následující.  
  
|Krok|Šablonu návrhu: když se stane|Šablona běhu: když se stane|  
|----------|--------------------------------------------|-----------------------------------------|  
|Kód je generován z textové šablony.<br /><br /> Chyby v direktivách, Neshoda nebo disordered `<#…#>` značky.|Když uložíte šablonu nebo volání transformací textu.|Když uložíte šablonu nebo volání transformací textu.|  
|Kompilace generovaného kódu.<br /><br /> Chyby kompilace v kódu šablony.|Ihned po předchozím kroku.|Spolu s kódu aplikace.|  
|Kód se spustí.<br /><br /> Běhové chyby v kódu šablony.|Ihned po předchozím kroku.|Když vaše aplikace se spustí a volá kód šablony.|  
  
 Ve většině případů čísel řádků v kódu šablony jsou uvedeny v chybové zprávě. Když zprávy o chybách odkazuje na dočasný název souboru, obvyklou příčinou je neshoda závorky v kódu textové šablony.  
  
 Můžete nastavit zarážky v textových šablonách a ladění obvyklým způsobem.  
  
## <a name="common-errors-and-fixes"></a>Běžné chyby a opravy  
 Následující tabulka uvádí nejběžnější chyby a jejich opravy.  
  
|Chybová zpráva|Popis|Řešení|  
|-------------------|-----------------|--------------|  
|Nepovedlo se načíst základní třídu{0}"ze které transformace třída dědí.|Nastane, pokud nemůžete najít základní třída zadaná v `inherits` parametr v direktivě šablony. Zpráva obsahuje číslo řádku – direktiva šablony.|Ujistěte se, že dané třídy existuje a zda sestavení, který existuje ve službě je zadán v direktivě sestavení.|  
|Nepovedlo se přeložit text zahrnutí pro soubor:{0}|Nastane, pokud nemůžete najít zahrnuty šablony. Zpráva obsahuje název požadované zahrnutého souboru.|Ujistěte se, že cesta k souboru je relativní vzhledem k původní šablony cesty, nebo, že se soubor nachází v umístění, který je zaregistrován u hostitele nebo, že je úplná cesta k souboru.|  
|Při inicializaci objektu transformace byly vygenerovány chyby. Transformace se nespustí.|Nastane, pokud "Initialize()" třídy transformace se nezdařila nebo vrátí hodnotu false.|Kód ve funkci Initialize() pochází z transformace základní třída zadaná v \<#@template#> a z procesorů pro direktivy. Chyba, která způsobila inicializace pravděpodobně selhání je v seznamu chyb. Zjistěte, proč byl neúspěšný. Můžete vyhledat na skutečné generovaný kód Initialize() pomocí následujících postupů, chcete-li ladit šablonu.|  
|Sestavení '{0}"pro procesor direktiv"{1}"neudělila sada oprávnění FullTrust. Jenom důvěryhodná sestavení můžou poskytovat procesory direktiv. Tento procesor direktiv se nenačte.|Vyvolá se v případě systému nejsou udělena oprávnění FullTrust k sestavení obsahujícímu procesor direktiv. Zpráva obsahuje název sestavení a název procesor direktiv.|Ujistěte se, že používáte jenom důvěryhodná sestavení v místním počítači.|  
|Cesta "{0}' musí být místní na tomto počítači nebo součástí zóny důvěryhodných serverů.|Vyvolá se v případě direktiva nebo – direktiva assembly odkazuje na soubor, který není na místním počítači nebo na vaší síti důvěryhodné zóny.|Ujistěte se, že je adresář, kde se nacházejí direktiva nebo direktivy sestavení do zóny důvěryhodných serverů. Síťovému adresáři můžete přidat do zóny důvěryhodných serverů pomocí aplikace Internet Explorer.|  
|Více chyby syntaxe, například "Neplatný token ' catch'" nebo "obor názvů nemůže přímo obsahovat členy"|Příliš mnoho uzavírací složené závorky v kódu šablony. Kompilátor je matoucí ho pomocí standardní generování kódu.|Zkontrolujte číslo ukončení složené závorky a hranaté závorky v kódu oddělovače.|  
|Smyčky nebo podmínky nejsou zkompilovat nebo provést správně. Příklad: `<#if (i>10)#> Number is: <#= i #>`.<br /><br /> Tento kód vracel vždy hodnotu jsem. Pouze "číslo je:" je podmíněný.|V jazyce C# vždy používejte složené závorky ohraničit textové bloky, které jsou vložené řídicí příkazy.|Přidat složené závorky: `<#if (i>10) { #>    Number is: <#= i #><# } #>`.|  
|"Výraz je příliš složitý" při zpracování šablony návrhu nebo kompilaci (předzpracovaná) šablona modulu runtime.<br /><br /> [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] přestává pracovat, při pokusu o zkontrolovat kód vygenerovaný šablonu modulu runtime.|Textový blok je příliš dlouhý. Bloky textu T4 převede na výraz zřetězení řetězců s jeden řetězcový literál pro každý řádek šablony. Bloky velmi dlouhý text můžete překročení omezení velikosti kompilátoru.|Rozdělte dlouhé textový blok s blok výrazu jako:<br /><br /> `<#= "" #>`|  
  
## <a name="warning-descriptions-and-fixes"></a>Popis upozornění a opravy  
 Následující tabulka uvádí nejběžnější upozornění spolu s opravami, pokud je k dispozici.  
  
|Zpráva upozornění|Popis|Řešení|  
|---------------------|-----------------|--------------|  
|Načítání souboru zahrnutí "{0}' vrátil hodnotu null nebo prázdný řetězec.|Nastane, pokud je prázdný soubor šablony textu. Zpráva obsahuje název souboru souboru.|Odebrat direktivy include nebo Ujistěte se, že soubor má nějaký obsah.|  
|Kompilování transformace:|Připojí na začátek tohoto řetězce pro všechny chyby nebo upozornění pocházející z kompilátoru při kompilaci transformace. Tento řetězec znamená, že kompilátor došlo k chybě nebo upozornění.|Pokud máte potíže najít knihovnu DLL, budete muset zadat úplnou cestu nebo silný plně kvalifikovaný název, pokud knihovna DLL v mezipaměti GAC.|  
|Parametr "{0}' již v direktivě existuje. Duplicitní parametr bude ignorován.|Nastane, pokud parametr je zadán více než jednou v direktivě. Zpráva obsahuje název parametru a číslo řádku direktivy.|Odeberte duplicitní parametr.|  
|Došlo k chybě při načítání souboru zahrnutí "{0}". Direktivy include se bude ignorovat.|Nastane, pokud nemůže najít soubor zadaný v `include` směrnice. Zpráva obsahuje název souboru a číslo řádku direktivy.|Ujistěte se, že tento soubor existuje ve stejném adresáři jako původní soubor textové šablony nebo v jednom z adresáře vložených souborů, které jsou registrovány hostitele.|  
|Pro třídu transformace byla zadána neplatná základní třída. Základní třída musí být odvozen od Microsoft.VisualStudio.TextTemplating.TextTransformation.|Nastane, když `inherits` parametr v direktivě šablony určuje třídu, která není odvozena od `TextTransformation`. Zpráva obsahuje číslo řádku – direktiva šablony.|Zadejte třídu, která je odvozena z `TextTransformation`.|  
|V direktivě 'šablony' byla zadána neplatná jazyková verze. Jazyková verze musí být ve formátu "xx-XX". Se používá invariantní jazyková verze.|Nastane, pokud je nesprávně zadán parametr jazykové verze v direktivě šablony. Zpráva obsahuje číslo řádku – direktiva šablony.|Změňte parametr jazykové verze na platná jazyková verze ve formátu "xx-XX".|  
|Neplatná ladicí hodnota "{0}' byl zadán v direktivě šablony. Ladicí hodnota musí být "true" nebo "false". Použije se výchozí hodnotu "false".|Nastane, když `debug` je nesprávně zadán parametr v direktivě šablony. Zpráva obsahuje číslo řádku – direktiva šablony.|Nastavte parametr ladění "true" nebo "false".|  
|Neplatná hodnota HostSpecific "{0}' byl zadán v direktivě šablony. Hodnota HostSpecific musí být "true" nebo "false". Použije se výchozí hodnotu "false".|Vyvolá se při parametr do konkrétního hostitele `template` nesprávně zadána direktiva. Zpráva obsahuje číslo řádku – direktiva šablony.|Nastavte parametr specifický pro hostitele na "true" nebo "false".|  
|Neplatný jazyk "{0}' byl zadán v direktivě 'šablony'. Jazyk musí být buď "C" nebo "VB". Použije se výchozí hodnota "C".|Nastane, pokud je zadán nepodporovaný jazyk v `template` směrnice. Pouze "C" nebo "VB" jsou povoleny (malých písmen). Zpráva obsahuje číslo řádku – direktiva šablony.|Nastavte `language` parametr v direktivě šablony na "C" nebo "VB".|  
|V šabloně bylo nalezeno více direktiv výstupu. Budou ignorovány všechny kromě první z nich.|Vyvolá se při více `output` direktivy jsou uvedeny v souboru šablony. Zpráva obsahuje číslo řádku směrnice duplicitním výstupem.|Odebrat duplicitní `output` direktivy.|  
|V šabloně bylo nalezeno více direktiv šablony. Budou ignorovány všechny kromě první z nich. Více parametrů direktivy šablony by měl být zadán v rámci jedné direktivy šablony.|Nastane, pokud zadáte více `template` direktivy v souboru šablony textu (včetně zahrnuté soubory). Zpráva obsahuje číslo řádku směrnice duplikovat šablonu.|Agregovat různých `template` direktivy do jedné `template` směrnice.|  
|Nebyl určen žádný procesor pro direktivu s názvem "{0}". Direktiva se bude ignorovat.|Nastane, pokud zadáte `custom` směrnice, ale neposkytují `processor` atribut. Zpráva obsahuje název směrnice a číslo řádku.|Zadejte `processor` atribut s názvem `directive` procesoru pro direktivu.|  
|Procesor s názvem "{0}"nebyl nalezen pro direktivu s názvem"{1}". Direktiva se bude ignorovat.|Nastane, pokud systém nemůže najít `directive` procesoru, které jste zadali v rámci `custom` směrnice. Zpráva obsahuje název direktivy, procesor název a číslo řádku direktivy.|Nastavte `processor` atribut v direktivě název procesor direktiv.|  
|Povinný parametr "{0}"pro direktivu"{1}' nebyl nalezen. Direktiva se bude ignorovat.|Vyvolá se v případě systému neposkytuje direktiv povinný parametr. Zpráva obsahuje název parametru chybí název směrnice a číslo řádku.|Zadejte parametr chybí.|  
|Procesor s názvem "{0}"nepodporuje direktivu s názvem"{1}". Direktiva se bude ignorovat.|Nastane, pokud procesor direktiv nepodporuje direktivu. Zpráva obsahuje název a číslo řádku porušilo směrnice spolu s názvem procesor direktiv.|Opravte název direktivy.|  
|Direktiva zahrnutí souboru "{0}' způsobuje nekonečnou smyčku.|Pokud cyklické direktiv zadávají (například soubor obsahuje soubor B, který obsahuje soubor A).|Nezadávejte cyklické direktiv.|  
|Spouštění transformace:|Připojí na začátek tohoto řetězce pro všechny chyby nebo upozornění, které jsou generovány při spuštění transformace.|Nelze použít.|  
|V rámci bloku byla nalezena neočekávaná počáteční nebo koncová značka. Ujistěte se, že jste nenapsali počáteční nebo koncová značka. proto, že nemáte žádné vnořené bloky v šabloně.|Zobrazí, když máte neočekávanou \<# nebo #>. To znamená pokud máte \<# po jiné otevřít značky, které ještě nebyly uzavřeny, nebo můžete mít #> když neexistuje žádná neuzavřený otevřete značka před ní. Zpráva obsahuje číslo řádku neodpovídající značky.|Buď odeberte neodpovídající počáteční nebo koncová značka, nebo použijte řídicí znak.|  
|Direktiva byla zadána v nesprávném formátu. Direktiva se bude ignorovat. Zadejte prosím direktivu ve formátu `<#@ name [parametername="parametervalue"]*  #>`|Zobrazit analyzátorem, pokud není zadán direktivu ve správném formátu. Zpráva obsahuje číslo řádku nesprávné směrnice.|Ujistěte se, všechna direktivy jsou ve formě `<#@ name [parametername="parametervalue"]*  #>`. Další informace najdete v tématu [direktivy textové šablony T4](../modeling/t4-text-template-directives.md).|  
|Nepovedlo se načíst sestavení '{0}"pro registrovaný procesor direktiv"{1}.<br /><br /> {2}|Nastane, pokud procesor direktiv nebylo možné načíst podle hostitele. Zpráva identifikuje sestavení k dispozici pro procesor direktiv a název procesor direktiv.|Ujistěte se, že je procesor direktiv správně zaregistrován a zda existuje sestavení.|  
|Nepovedlo se najít typ "{0}'v sestavení'{1}"pro registrovaný procesor direktiv"{2}.<br /><br /> {3}|Nastane, pokud typ procesoru direktiv nelze načíst z příslušného sestavení. Zpráva obsahuje název typu, sestavení a směrnice procesoru.|Vshost zjistí procesor direktiv informace (název, sestavení a typu) v registru. Ujistěte se, že je správně zaregistrován procesoru direktiv a zda existuje typ v sestavení.|  
|Došlo k potížím při načítání sestavení '{0}.|Nastane, když dojde k potížím při načítání sestavení. Zpráva obsahuje název sestavení.|Můžete zadat sestavení, které mají být načteny v \<@# assembly #> direktivy a procesory direktiv. Chybová zpráva, která následuje tento řetězec by měl poskytují další data o proč načtení sestavení se nezdařilo.|  
|Došlo k potížím při vytváření a inicializaci procesoru pro direktivu s názvem "{1}". Typ procesoru je {0}. Direktiva se bude ignorovat.|Vyvolá se v případě systému nelze vytvořit nebo inicializaci procesoru direktiv. Zpráva obsahuje název a řádek číslo směrnice a typ procesoru.|Nezapomeňte použít správný procesor direktiv, a že procesor direktiv veřejný výchozí konstruktor. V opačném případě použijte možnosti ladění a zjistěte, proč se nedaří metodu Initialize() procesoru direktiv. Další informace najdete v tématu [řešení potíží s textových šablon](../modeling/debugging-a-t4-text-template.md).|  
|Došlo k výjimce při zpracovávání direktivy s názvem "{0}".|Nastane, pokud procesor direktiv vyvolá výjimku při zpracovávání direktivy.|Ujistěte se, že jsou správné parametry, které mají procesor direktiv.|  
|Hostitel vyvolal výjimku při pokusu o přeložení odkazu na sestavení '{0}".|Nastane, pokud hostitel vyvolá výjimku, když se ho pokusí přeložit odkaz na sestavení. Zpráva obsahuje sestavení odkazují na řetězce.|Sestavení pocházet odkazy \<@# assembly #> direktivy a z procesorů pro direktivy. Ujistěte se, že parametr "name" zadané v parametru sestavení je správná.|  
|Pokus o určení nepodporované {1} hodnotu "{0}" pro – direktiva {2}|Nastává při RequiresProvidesDirectiveProcessor (všechny naše vygenerované procesory direktiv jsou odvozeny z něj), když zadáte nepodporované vyžadovaný nebo poskytovaný argument.|Ujistěte se, že názvy v name = "" páry hodnot součástí vyžaduje a poskytuje parametry jsou správné.|



