---
title: Ladění textové šablony T4
description: Chcete-li ladit textovou šablonu návrhu, uložte soubor textové šablony a zvolte možnost ladit šablonu T4 v místní nabídce souboru v Průzkumník řešení.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, troubleshooting
- text templates, debugging
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b197fd52972162acbc6e7d6882507f943b2a560c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99935349"
---
# <a name="debugging-a-t4-text-template"></a>Ladění textové šablony T4
Můžete nastavit zarážky v textových šablonách. Chcete-li ladit textovou šablonu návrhu, uložte soubor textové šablony a zvolte možnost **ladit šablonu T4** v místní nabídce souboru v Průzkumník řešení. Chcete-li ladit textovou šablonu run-time, stačí ladit aplikaci, do které patří.

 Chcete-li ladit textovou šablonu, měli byste pochopit kroky procesu transformace šablony. V rámci každého kroku může dojít k různým typům chyb. Postup je následující.

|Krok|Šablona v době návrhu: když dojde|Šablona run-time: když se stane|
|-|-|-|
|Kód je vygenerován z textové šablony.<br /><br /> Chyby v direktivách nebo neodpovídající nebo neuspořádané `<#...#>` značky.|Když uložíte šablonu nebo vyvolá transformaci textu.|Když uložíte šablonu nebo vyvolá transformaci textu.|
|Generovaný kód je zkompilován.<br /><br /> Chyby kompilace v kódu šablony.|Hned za předchozím krokem.|Spolu s kódem aplikace.|
|Spuštění kódu.<br /><br /> Běhové chyby ve vašem kódu šablony.|Hned za předchozím krokem.|Když vaše aplikace běží a vyvolá kód šablony.|

 Ve většině případů jsou čísla řádků v kódu šablony uvedena v hlášení o chybách. Pokud zpráva o chybách odkazuje na dočasný název souboru, Obvyklá příčina je neshoda závorek v kódu textové šablony.

 Můžete nastavit zarážky v textových šablonách a ladit obvyklým způsobem.

## <a name="common-errors-and-fixes"></a>Běžné chyby a opravy
 V následující tabulce jsou uvedeny nejběžnější chyby a jejich opravy.

|Chybová zpráva|Description|Řešení|
|-|-|-|
|Nepodařilo se načíst základní třídu, {0} ze které dědí třída transformace.|Nastane, pokud nemůžete najít základní třídu zadanou v `inherits` parametru v direktivě šablony. Zpráva poskytuje číslo řádku direktivy šablony.|Ujistěte se, že zadaná třída existuje a že sestavení, v němž existuje, je zadáno v direktivě Assembly.|
|Nepovedlo se přeložit text zahrnutí pro soubor:{0}|Vyvolá se v případě, že nemůžete najít zahrnutou šablonu. Zpráva obsahuje název požadovaného souboru k zahrnutí.|Ujistěte se, že cesta k souboru je relativní vzhledem k původní cestě k šabloně, nebo že se soubor nachází v umístění, které je zaregistrované u hostitele, nebo jestli existuje úplná cesta k souboru.|
|Při inicializaci objektu transformace byly vygenerovány chyby. Transformace se nespustí.|Nastane, pokud se nezdařila hodnota Initialize () třídy transformace nebo vrátila hodnotu false.|Kód ve funkci Initialize () přichází ze základní třídy transformace zadané v \<#@template#> direktivě a v procesorech direktiv. Chyba, která způsobila selhání inicializace, pravděpodobně je v seznamu chyb. Zjistěte, proč došlo k chybě. Můžete se podívat na vlastní generovaný kód pro inicializaci () podle pokynů pro ladění šablony.|
|Sestavení {0} pro procesor direktiv se {1} neudělilo sadě oprávnění FullTrust. Procesory direktiv můžou poskytovat jenom důvěryhodná sestavení. Tento procesor direktiv se nenačte.|Vyvolá se v případě, že systém neudělí oprávnění FullTrust k sestavení obsahujícímu procesor direktiv. Zpráva poskytuje název sestavení a název procesoru direktiv.|Ujistěte se, že používáte pouze důvěryhodná sestavení v místním počítači.|
|Cesta ' {0} ' musí být buď místní k tomuto počítači nebo část vaší důvěryhodné zóny.|Vyvolá se v případě, že direktiva nebo direktiva sestavení odkazuje na soubor, který není na vašem místním počítači nebo v důvěryhodné zóně vaší sítě.|Ujistěte se, že adresář, ve kterém jsou umístěny direktivy direktivy nebo sestavení, je ve vaší důvěryhodné zóně. Pomocí aplikace Internet Explorer můžete přidat síťový adresář do důvěryhodné zóny.|
|Více syntaktických chyb, jako je například "neplatný token" catch "nebo" obor názvů nemůže přímo obsahovat členy "|V kódu šablony je příliš mnoho uzavíracích závorek. Kompilátor je matoucí pomocí standardního kódu generování.|Ověřte počet uzavíracích závorek a závorek uvnitř oddělovačů kódu.|
|Smyčky nebo podmíněné výrazy nejsou zkompilovány nebo provedeny správně. Příklad: `<#if (i>10)#> Number is: <#= i #>`.<br /><br /> Tento kód vždy vyprodukuje hodnotu i. Podmínkou je pouze "číslo je:".|V jazyce C# vždy používejte složené závorky k obklopení textových bloků, které jsou vloženy do řídicích příkazů.|Přidat složené závorky: `<#if (i>10) { #>    Number is: <#= i #><# } #>` .|
|Výraz je moc složitý při zpracování šablony návrhu nebo kompilace šablony modulu runtime (předzpracovaného).<br /><br /> Visual Studio přestane pracovat při pokusu o kontrolu kódu generovaného šablonou modulu runtime.|Textový blok je příliš dlouhý. T4 převede textové bloky na výraz zřetězení řetězců s jedním řetězcovým literálem pro každý řádek šablony. Dlouhé bloky textu můžou přeměnit limity velikosti kompilátoru.|Rozdělte blok dlouhého textu pomocí bloku výrazu, jako je:<br /><br /> `<#= "" #>`|

## <a name="warning-descriptions-and-fixes"></a>Popisy a opravy upozornění
 Následující tabulka uvádí nejběžnější upozornění společně s opravami, pokud jsou k dispozici.

|Zpráva upozornění|Description|Řešení|
|-|-|-|
|Načtení souboru zahrnutí {0} vrátilo hodnotu null nebo prázdný řetězec.|Nastane, pokud je vložený textový soubor šablony prázdný. Zpráva obsahuje název souboru zahrnutého souboru.|Buď odeberte direktivu include, nebo se ujistěte, že soubor obsahuje nějaký obsah.|
|Kompilace transformace:|Předá tento řetězec všem chybám nebo varováním, které pocházejí z kompilátoru při kompilování transformace. Tento řetězec znamená, že kompilátor vyvolal chybu nebo upozornění.|Pokud máte problém s hledáním knihovny DLL, může být nutné zadat úplnou cestu nebo plně kvalifikovaný silný název, pokud je knihovna DLL v mezipaměti GAC.|
|Parametr {0} již v direktivě existuje. Duplicitní parametr se bude ignorovat.|Vyvolá se v případě, že je parametr zadán více než jednou v direktivě. Zpráva poskytuje název parametru a číslo řádku direktivy.|Odeberte specifikaci duplicitního parametru.|
|Při načítání souboru zahrnutí došlo k chybě {0} . Direktiva include bude ignorována.|Vyvolá se v případě, že nemůžete najít soubor určený v `include` direktivě. Zpráva poskytuje název souboru a číslo řádku direktivy.|Ujistěte se, že soubor zahrnutí existuje buď ve stejném adresáři jako původní textový soubor šablony, nebo v jednom z adresářů, které jsou zaregistrované u hostitele.|
|Pro třídu transformace byla zadána neplatná základní třída. Základní třída musí být odvozena od třídy Microsoft. VisualStudio. TextTemplating. TextTransformation.|Nastane, pokud `inherits` parametr v direktivě šablony určuje třídu, která nedědí z `TextTransformation` . Zpráva poskytuje číslo řádku direktivy šablony.|Určete třídu, která je odvozena z `TextTransformation` .|
|V direktivě Template byla zadána neplatná jazyková verze. Jazyková verze musí být ve formátu "XX-XX". Použije se invariantní jazyková verze.|Vyvolá se v případě, že je parametr jazykové verze v direktivě šablony zadán nesprávně. Zpráva poskytuje číslo řádku direktivy šablony.|Změňte parametr jazykové verze na platnou jazykovou verzi ve formátu "XX-XX".|
|{0}V direktivě šablony byla zadána neplatná hodnota pro ladění. Hodnota ladění musí být buď true, nebo false. Použije se výchozí hodnota false (NEPRAVDA).|Vyvolá se v případě, že `debug` je parametr v direktivě šablony nesprávně zadán. Zpráva poskytuje číslo řádku direktivy šablony.|Nastavte parametr Debug na hodnotu "true" nebo "false".|
|{0}V direktivě šablony byla zadána neplatná hodnota hostspecific. Hodnota HostSpecific musí být buď true, nebo false. Použije se výchozí hodnota false (NEPRAVDA).|Vyvolá se v případě, že je parametr specifický pro hostitele v `template` direktivě zadán nesprávně. Zpráva poskytuje číslo řádku direktivy šablony.|Nastavte parametr specifický pro hostitele na hodnotu "true" nebo "false".|
|{0}V direktivě template byl zadán neplatný jazyk. Jazyk musí být buď C#, nebo VB. Použije se výchozí hodnota C#.|Nastane, pokud je v direktivě zadán nepodporovaný jazyk `template` . Jsou povoleny pouze jazyky C# nebo VB (nerozlišuje velká a malá písmena). Zpráva poskytuje číslo řádku direktivy šablony.|Nastavte `language` parametr v direktivě Template na "C#" nebo "VB".|
|V šabloně bylo nalezeno více direktiv výstupu. Všechny kromě prvního ale budou ignorovány.|Vyvolá se v případě, že je `output` v souboru šablony zadáno více direktiv. Zpráva poskytuje číslo řádku pro duplicitní výstupní direktivu.|Odeberte duplicitní `output` direktivy.|
|V šabloně bylo nalezeno více direktiv šablony. Všechny kromě prvního ale budou ignorovány. V rámci jedné direktivy šablony by mělo být zadáno více parametrů direktivy šablony.|Nastane, pokud zadáte více `template` direktiv v rámci souboru textové šablony (včetně zahrnutých souborů). Zpráva poskytuje číslo řádku duplicitní direktivy šablony.|Seskupte různé `template` direktivy do jedné `template` direktivy.|
|Pro direktivu s názvem ' ' nebyl zadán žádný procesor {0} . Direktiva bude ignorována.|Nastane, pokud zadáte `custom` direktivu, ale nezadáte `processor` atribut. Zpráva poskytuje název direktivy a číslo řádku.|Zadejte `processor` atribut s názvem `directive` procesoru pro tuto direktivu.|
|Procesor s názvem {0} ' ' nebyl nalezen pro direktivu s názvem ' {1} '. Direktiva bude ignorována.|Vyvolá se v případě, že systém nemůže najít `directive` procesor, který jste zadali v rámci `custom` direktivy. Zpráva poskytuje název direktivy, název procesoru a číslo řádku direktivy.|Nastavte `processor` atribut v direktivě na název procesoru direktiv.|
|Požadovaný parametr {0} pro direktivu nebyl {1} nalezen. Direktiva bude ignorována.|Vyvolá se v případě, že systém neposkytne požadovaný parametr direktivy. Zpráva poskytuje název chybějícího parametru, název direktivy a číslo řádku.|Zadejte chybějící parametr.|
|Procesor s názvem nepodporuje {0} direktivu s názvem {1} . Direktiva bude ignorována.|Vyvolá se v případě, že procesor direktiv nepodporuje direktivu. Zpráva poskytuje název a číslo problematické direktivy spolu s názvem procesoru direktiv.|Opravte název direktivy.|
|Direktiva include pro soubor {0} způsobuje nekonečnou smyčku.|Zobrazuje se, pokud jsou zadány cyklické direktivy include (například File A zahrnuje soubor B, který obsahuje soubor A).|Nezadávejte cyklické direktivy include.|
|Spouštění transformace:|Dořadí tento řetězec ke všem chybám nebo varováním, které jsou generovány při spuštění transformace.|Neužívá se.|
|V rámci bloku byla nalezena neočekávaná počáteční nebo koncová značka. Ujistěte se, že jste nezadali počáteční nebo koncovou značku a že v šabloně nemáte žádné vnořené bloky.|Zobrazí se v případě neočekávaného \<# or #> . To znamená, že pokud máte, \<# after another open tag that has not been closed, or you have a #> když před ním nezůstane žádná neuzavřená otevřená značka. Zpráva poskytuje číslo řádku neodpovídající značky.|Buď odeberte neshodnou počáteční nebo koncovou značku, nebo použijte řídicí znak.|
|Byla zadána direktiva v nesprávném formátu. Direktiva bude ignorována. Zadejte prosím direktivu ve formátu. `<#@ name [parametername="parametervalue"]*  #>`|Zobrazeno analyzátorem, pokud není zadána direktiva ve správném formátu. Zpráva poskytuje číslo řádku nesprávné direktivy.|Ujistěte se, že všechny direktivy jsou ve formátu `<#@ name [parametername="parametervalue"]*  #>` . Další informace naleznete v tématu [direktivy textové šablony T4](../modeling/t4-text-template-directives.md).|
|Načtení sestavení ' {0} ' pro registrovaný procesor direktiv ' ' se nezdařilo. ' {1} '<br /><br /> {2}|Vyvolá se v případě, že hostitel nemůže načíst procesor direktiv. Zpráva identifikuje sestavení poskytnuté pro procesor direktiv a název procesoru direktiv.|Ujistěte se, že je správně zaregistrován procesor direktiv a zda sestavení existuje.|
|Nepovedlo se najít typ {0} v sestavení {1} pro registrovaný procesor direktiv. {2}<br /><br /> {3}|Nastane, pokud se nepovedlo načíst typ procesoru direktiv z jeho sestavení. Zpráva poskytuje název typu, sestavení a procesoru direktiv.|VSHost vyhledá v registru informace o procesoru direktiv (název, sestavení a typ). Ujistěte se, že je správně zaregistrován procesor direktiv a zda typ existuje v sestavení.|
|Při načítání sestavení došlo k {0} problému.|Nastane, pokud dojde k potížím při načítání sestavení. Zpráva poskytuje název sestavení.|Můžete určit sestavení, která mají být načtena do \<@#assembly#> direktiv a pomocí procesorů směrnice. Chybová zpráva, která následuje tento řetězec, by měla poskytnout více dat pro důvody, proč selhalo načtení sestavení.|
|Došlo k potížím při vytváření a inicializaci procesoru pro direktivu s názvem {1} . Typ procesoru je {0} . Direktiva bude ignorována.|Vyvolá se v případě, že systém nemohl vytvořit nebo inicializovat procesor direktiv. Zpráva poskytuje název a číslo řádku direktivy a typ procesoru.|Ujistěte se, že používáte správný procesor direktiv a že má procesor direktivy veřejný výchozí konstruktor. V opačném případě použijte možnosti ladění, abyste zjistili, proč metoda Initialize () procesoru direktivy selhala. Další informace najdete v tématu [Poradce při potížích s textovými šablonami](../modeling/debugging-a-t4-text-template.md).|
|Při zpracovávání direktivy s názvem ' ' byla vyvolána výjimka {0} .|Vyvolá se v případě, že procesor direktiv vyvolá výjimku při zpracování direktivy.|Ujistěte se, že parametry procesoru direktiv jsou správné.|
|Hostitel vyvolal výjimku při pokusu o překlad odkazu na sestavení {0} .|Vyvolá se v případě, že hostitel vyvolá výjimku, když se pokusí přeložit odkaz na sestavení. Zpráva poskytuje řetězec odkazu na sestavení.|Odkazy na sestavení pocházejí ze \<@#assembly#> direktiv a ze procesorů direktiv. Ujistěte se, že parametr Name zadaný v parametru sestavení je správný.|
|Byl proveden pokus o zadání nepodporované {1} hodnoty {0} pro direktivu. {2}|Vyvolá se v RequiresProvidesDirectiveProcessor (všechny naše vygenerované procesory direktiv z něho odvozené), když zadáte nepodporovaný argument vyžaduje nebo poskytne argument.|Ujistěte se, že názvy v parametrech název = ' hodnota ' zadané v parametrech vyžaduje a poskytuje správné.|
