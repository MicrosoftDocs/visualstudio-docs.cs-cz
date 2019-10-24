---
title: Registrace starší verze jazyka Jazyka2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, language services
- language services, registry information
- registry, language services
ms.assetid: ca312aa3-f9f1-4572-8553-89bf3a724deb
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2e1cb2d8193d0ffa6285357634b8bcab549ecbf6
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72724750"
---
# <a name="registering-a-legacy-language-service"></a>Registrace služby starší verze jazyka
V následujících částech najdete seznam položek registru pro různé možnosti jazykové služby, které jsou dostupné v [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

 V následujícím seznamu položek registru se jako *kořenový adresář nástroje vs reg* rovná HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio \\*x. y*, kde *X. y* je číslo verze [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

## <a name="registry-entries-for-language-service-options"></a>Položky registru pro možnosti služby jazyka
 V nástroji *vs reg root*\Languages\Language Services \\: klíč*názvu jazyka* může obsahovat následující hodnoty.

|Name|Typ|Rozsah|Popis|
|----------|----------|-----------|-----------------|
|(Výchozí)|REG_SZ|*\<GUID >*|Identifikátor GUID jazykové služby|
|LangResID|REG_DWORD|0x0 – 0xFFFF|Identifikátor prostředku řetězce (ResID) pro lokalizovaný textový název jazyka.|
|Balíček|REG_SZ|*\<GUID >*|Identifikátor GUID VSPackage|
|ShowCompletion|REG_DWORD|0-1|Určuje, zda jsou v dialogovém okně **Možnosti** povoleny možnosti **dokončování příkazů** .|
|ShowSmartIndent|REG_DWORD|0-1|Určuje, jestli je povolená možnost vybrat **inteligentní** odsazení v dialogovém okně **Možnosti** .|
|RequestStockColors|REG_DWORD|0-1|Určuje, zda se pro barevná klíčová slova použijí vlastní nebo výchozí barvy.|
|ShowHotURLs|REG_DWORD|0-1|Určuje, jestli uživatel může kliknout na adresy URL.|
|Výchozí pro nehot adresy URL|REG_DWORD|0-1|Určuje počáteční nastavení pro možnost **navigace URL s jedním kliknutím** v dialogovém okně **Možnosti** .|
|DefaultToInsertSpaces|REG_DWORD|0-1|Určuje, jestli má jazyková služba jako výchozí možnost tabulátoru "vložit mezery".|
|ShowDropdownBarOption|REG_DWORD|0-1|Povolí nebo zakáže možnost **navigační panel** v dialogovém okně **Možnosti** , které zobrazuje nebo skrývá **navigační panel**.|
|Pouze jedno okno kódu|REG_DWORD|0-1|Povolí nebo zakáže výběr **nového okna** v nabídce **okna** pro službu jazyka.|
|EnableAdvancedMembersOption|REG_DWORD|0-1|Povolí nebo zakáže nastavení dialogového okna **Možnosti** pro **skrytí rozšířených členů**.|
|Podpora CF_HTML|REG_DWORD|0-1|Určuje, zda editor umožňuje kopírování a vkládání dat HTML.|
|EnableLineNumbersOption|REG_DWORD|0-1|Určuje, zda jsou v dialogovém okně **Možnosti** pro službu jazyka povoleny možnosti **číslování řádků** .|
|HideAdvancedMembersByDefault|REG_DWORD|0-1|Určuje, zda jsou v seznamech dokončování skryti pokročilí členové, například soukromá pole.|
|ShowBraceCompletion|REG_DWORD|0-1|Určuje, zda je možnost **dokončování složených závorek** v dialogovém okně **Možnosti** povolena.|

### <a name="example"></a>Příklad

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\
  Languages\
    Language Services\
      C/C++\
        (Default)             = reg_sz:{B2F072B0-ABC1-11D0-9D62-00C04FD9DFD9}
        LangResID             = reg_dword:0x00000000
        Package               = reg_sz:{8C2EA640-ABC1-11D0-9D62-00C04FD9DFD9}
        ShowCompletion        = reg_dword:0x00000001
        ShowSmartIndent       = reg_dword:0x00000001
        ShowDropdownBarOption = reg_dword:0x00000001
```

## <a name="registry-entries-for-debugger-languages-options"></a>Položky registru pro možnosti jazyků ladicího programu
 \Languages\Language Services \\*GUID*\ Key může obsahovat následující hodnoty: jazyky *vs Reg root* *\\ Services*

|Name|Typ|Rozsah|Popis|
|----------|----------|-----------|-----------------|
|(Výchozí)|REG_SZ|text|Výchozí hodnota se dá použít k dokumentování názvu jazyka. Název tohoto klíče je identifikátor GUID vyhodnocovacího filtru výrazů, který má odpovídající položku v nástroji *\<VS reg Root >* \AD7Metrics\Expression hodnotitele.|

### <a name="example"></a>Příklad

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\
  Languages\
    Language Services\
      C/C++\
        Debugger Languages\
          {3A12D0B7-C26C-11D0-B442-00A0244A1DD2}\
            (Default) = reg_sz:C++
```

## <a name="registry-entries-for-editor-tools-options"></a>Položky registru pro možnosti nástrojů editoru
 Klíče registru můžete přidat pod klíč EditorToolsOptions pro stránky vlastností a uzly vlastností. Tyto klíče a jejich hodnoty identifikují stránky vlastností v dialogovém okně **Možnosti** (v nabídce **nástroje** ), které se používají ke konfiguraci jazykové služby. V následujícím příkladu je *název stránky* název stránky vlastností a *název uzlu* je název uzlu ve stromové struktuře v dialogovém okně **Možnosti** . Položka stránky a položka uzlu musí být zadány samostatně.

|Name|Typ|Rozsah|Popis|
|----------|----------|-----------|-----------------|
|(Výchozí)|REG_SZ|ResID|Lokalizovaný zobrazovaný název této stránky možností. Název může být literální text nebo # `nnn`, kde `nnn` je ID prostředku řetězce v satelitní knihovně DLL zadaného rozhraní VSPackage.|
|Balíček|REG_SZ|*HLAVNÍCH*|Identifikátor GUID balíčku VSPackage, který implementuje tuto stránku možností.|
|Page|REG_SZ|*HLAVNÍCH*|Identifikátor GUID stránky vlastností, která má být vyvolána ze sady VSPackage voláním metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>. Pokud tato položka registru není k dispozici, klíč registru popisuje uzel, nikoli stránku.|

### <a name="example"></a>Příklad

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\
  Languages\
    Language Services\
      CSharp\
        EditorToolsOptions\
          Formatting\
            (Default) = reg_sz:#242
            Package   = reg_sz:{A066E284-DCAB-11D2-B551-00C04F68D4DB}
            General\
              (Default) = reg_sz:#255
              Package   = reg_sz:{A066E284-DCAB-11D2-B551-00C04F68D4DB}
              Page      = reg_sz:{3EB2CC0B-033E-4D75-B26A-B2362C25227E}
            Indentation\
              (Default) = reg_sz:#250
              Package   = reg_sz:{A066E284-DCAB-11D2-B551-00C04F68D4DB}
              Page      = reg_sz:{5E21D017-6D2A-4114-A1F1-C923F001CBBB}
            Newlines\
              (Default) = reg_sz:#253
              Package   = reg_sz:{A066E284-DCAB-11D2-B551-00C04F68D4DB}
              Page      = reg_sz:{607D8062-68D1-41E4-9A35-B5E7F14D0481}
```

## <a name="registry-entries-for-file-name-extension-options"></a>Položky registru pro možnosti přípony názvu souboru
 Položka pro příponu souboru by měla zahrnovat úvodní období, například ". myext".

|Name|Typ|Rozsah|Popis|
|----------|----------|-----------|-----------------|
|(Výchozí)|REG_SZ|*HLAVNÍCH*|Identifikátor GUID služby výchozí jazykové služby pro tento typ přípony názvu souboru.|

### <a name="example"></a>Příklad

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\
  Languages\
    File Extensions\
      .cpp\
        (Default) = {B2F072B0-ABC1-11D0-9D62-00C04FD9DFD9}
```

## <a name="registry-entries-for-editor-options"></a>Položky registru pro možnosti editoru
 Kořenový klíč \Editors sady *vs reg*může obsahovat následující hodnoty:

|Name|Typ|Rozsah|Popis|
|----------|----------|-----------|-----------------|
|(Výchozí)|REG_SZ|""|Nepoužívané sem můžete umístit své jméno pro dokumentaci.|
|DefaultToolboxTab|REG_SZ|""|Název karty panelu nástrojů, která má být nastavena na výchozí hodnotu, je-li Editor aktivní|
|DisplayName|REG_SZ|ResID|Název, který se má zobrazit v dialogovém okně **otevřít v programu** Název je ID prostředku řetězce nebo název ve standardním formátu.|
|ExcludeDefTextEditor|REG_DWORD|0-1|Používá se pro příkaz **otevřít v** nabídce. Pokud nechcete vypsat výchozí textový editor v seznamu dostupných editorů pro určitý typ souboru, nastavte tuto hodnotu na 1.|
|LinkedEditorGUID|REG_SZ|*\<GUID >*|Používá se pro libovolnou jazykovou službu, která může otevřít soubor s podporou znakové sady. Například když otevřete soubor. txt pomocí příkazu **otevřít pomocí** , jsou k dispozici možnosti pro použití editoru zdrojového kódu s kódováním i bez něj.<br /><br /> Identifikátor GUID zadaný v názvu podklíče je pro objekt pro vytváření editorů znakové sady. propojený identifikátor GUID zadaný v této konkrétní položce registru je pro objekt pro vytváření běžných editorů. Účelem této položky je, že pokud IDE neotevře soubor pomocí výchozího editoru, IDE se pokusí použít další Editor v seznamu. Tento další Editor by neměl být objekt pro vytváření editoru znakové sady, protože tento objekt pro vytváření editoru je v podstatě stejný jako objekt pro vytváření editoru, který se nezdařil.|
|Balíček|REG_SZ|*\<GUID >*|Identifikátor GUID VSPackage pro ResID zobrazovaného názvu|

### <a name="example"></a>Příklad

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\
  \Editors\
    {8281C572-2171-45AA-A642-7D8BC1662F1C}\
      (Default)            = reg_sz:Html Editor with Encoding
      DefaultToolboxTab    = reg_sz:HTML
      DisplayName          = reg_sz:#20101
      LinkedEditorGUID     = reg_sz:{C76D83F8-A489-11D0-8195-00A0C91BBEE3}
      Package              = reg_sz:{1B437D20-F8FE-11D2-A6AE-00104BCC7269}
```

## <a name="registry-entries-for-logical-view-options"></a>Položky registru pro možnosti logického zobrazení
 > Klíč \Editors \\*grafického uživatelského rozhraní editoru* *vs reg*může obsahovat následující hodnoty.

|Name|Typ|Rozsah|Popis|
|----------|----------|-----------|-----------------|
|(Výchozí)|REG_SZ||Nepoužívané.|
|*\<GUID >*|REG_SZ|""|Klíč k podporovaným logickým zobrazením. Můžete mít tolik z nich, kolik potřebujete. Název položky registru je to důležité, nikoli hodnota, která je vždy prázdným řetězcem.|

### <a name="example"></a>Příklad

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\
  \Editors\
    {8281C572-2171-45AA-A642-7D8BC1662F1C}\
      LogicalViews\
       (Default) = reg_sz:
       {7651a700-06e5-11d1-8ebd-00a0c90f26ea} = reg_sz:
       {7651a701-06e5-11d1-8ebd-00a0c90f26ea} = reg_sz:
       {7651a702-06e5-11d1-8ebd-00a0c90f26ea} = reg_sz:
       {7651a703-06e5-11d1-8ebd-00a0c90f26ea} = reg_sz:
```

## <a name="registry-entries-for-editor-extension-options"></a>Položky registru pro možnosti rozšíření editoru
 \Editors*identifikátor GUID \Extensions editoru* *vs reg*\\ může obsahovat následující hodnoty. Přípona názvu souboru nezahrnuje úvodní období.

|Name|Typ|Rozsah|Popis|
|----------|----------|-----------|-----------------|
|(Výchozí)|REG_SZ||Nepoužívané.|
|*\<ext >*|REG_DWORD|0 – 0xFFFFFFFF|Relativní priorita rozšíření. Pokud dva nebo více jazyků sdílí stejné rozšíření, je zvolen jazyk s vyšší prioritou.|

 Výchozí výběr aktuálního uživatele pro Editor je navíc uložen v HKEY_Current_User\Software\Microsoft\VisualStudio \\*X. Y*\Default editors \\*EXT*. Identifikátor GUID vybrané jazykové služby je ve vlastní položce. Tato akce má přednost pro aktuálního uživatele.

### <a name="example"></a>Příklad

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0\
  \Editors\
    {8281C572-2171-45AA-A642-7D8BC1662F1C}\
      Extensions\
       (Default) = reg_sz:
       *         = reg_dword:0x00000018
       html      = reg_dword:0x00000027
       shtm      = reg_dword:0x00000027
       shtml     = reg_dword:0x00000027
```

## <a name="registry-entries-for-managed-package-framework-language-service-options"></a>Položky registru pro možnosti služby jazyka Managed Package Framework
 Následující položky registru jsou specifické pro třídy služby jazyka Managed Package Framework (MPF). Tyto položky registru označují podporu ve službě jazyka pro různé funkce IntelliSense a další pokročilé funkce pro úpravy.

 Tyto položky registru jsou dostupné prostřednictvím třídy <xref:Microsoft.VisualStudio.Package.LanguagePreferences>.

|Name|Typ|Rozsah|Popis|
|----------|----------|-----------|-----------------|
|CodeSense|REG_DWORD|0-1|Podpora operací IntelliSense.|
|MatchBraces|REG_DWORD|0-1|Podpora pro párové dvojice jazyků, jako jsou složené závorky, kulaté závorky a závorky.|
|QuickInfo|REG_DWORD|0-1|Podpora funkce Rychlá informace technologie IntelliSense.|
|ShowMatchingBrace|REG_DWORD|0-1|Podpora zobrazení párové dvojice jazyků ve stavovém řádku.|
|MatchBracesAtCaret|REG_DWORD|0-1|Podpora pro zobrazení párů vyhovujících jazyků, obvykle prostřednictvím zvýraznění těchto dvou prvků.|
|MaxErrorMessages|REG_DWORD|0 – n|Maximální počet chyb, které mohou být zobrazeny v okně **Seznam chyb** .|
|CodeSenseDelay|REG_DWORD|0 – n|Počet milisekund do zpoždění před zahájením analýzy na pozadí pro operaci IntelliSense.|
|EnableAsyncCompletion|REG_DWORD|0-1|Podpora pro analýzu na pozadí.|
|EnableCommenting|REG_DWORD|0-1|Podpora pro komentování vybraných bloků textu a také vypovídá o podpoře pro odkomentování vybraného textu.|
|EnableFormatSelection|REG_DWORD|0-1|Podpora formátování textu, jako je automatické odsazení nebo úprava umístění složených závorek.|
|AutoOutlining|REG_DWORD|0-1|Podpora pro sbalení (oblasti, které se dají sbalit).|
|MaxRegions|REG_DWORD|0 – n|Maximální počet skrytých oblastí na soubor.|

```
ExampleHKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\
  Languages\
    Language Services\
      XML\
        (Default)             = reg_sz:{f6819a78-a205-47b5-be1c-675b3c7f0b8e}
        MatchBraces           = reg_dword:0x00000001
        QuickInfo             = reg_dword:0x00000001
        ShowMatchingBrace     = reg_dword:0x00000001
        MatchBracesAtCaret    = reg_dword:0x00000000
        MaxErrorMessages      = reg_dword:0x00000064
        CodeSenseDelay        = reg_dword:0x000001f4
        MaxRegions            = reg_dword:0x0000000a
```

## <a name="see-also"></a>Viz také:
- [Vývoj služby starší verze jazyka](../../extensibility/internals/developing-a-legacy-language-service.md)