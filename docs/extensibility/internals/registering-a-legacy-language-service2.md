---
title: Registrace služby staršího jazyka2 | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, language services
- language services, registry information
- registry, language services
ms.assetid: ca312aa3-f9f1-4572-8553-89bf3a724deb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2d9d13f301f6c04c0f7b14cc8c685f08b072ef84
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705891"
---
# <a name="registering-a-legacy-language-service"></a>Registrace služby starší verze jazyka
V následujících částech jsou uvedeny seznamy položek [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]registru pro různé možnosti jazykových služeb, které jsou k dispozici v aplikaci .

 V následujícím seznamu položek registru je *kořen v jazyce VS* Reg\\rovna HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio*X.Y*, kde *X.Y* je číslo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] verze.

## <a name="registry-entries-for-language-service-options"></a>Položky registru pro možnosti jazykové služby
 Kořenový *adresář VS*\Languages\Language Services\\Language*Name* key může obsahovat následující hodnoty.

|Name (Název)|Typ|Rozsah|Popis|
|----------|----------|-----------|-----------------|
|(Výchozí)|REG_SZ|*\<>IDENTIFIKÁTORGUID*|IDENTIFIKÁTOR GUID jazykové služby.|
|LangResID|REG_DWORD|0x0-0xffff|Identifikátor prostředku řetězce (ResID) pro lokalizovaný textový název jazyka.|
|Balíček|REG_SZ|*\<>IDENTIFIKÁTORGUID*|IDENTIFIKÁTOR GUID balíčku VSPackage.|
|Zobrazit dokončení|REG_DWORD|0-1|Určuje, zda jsou povoleny možnosti **dokončení výkazu** v dialogovém okně **Možnosti.**|
|ZobrazitInteligentníindent|REG_DWORD|0-1|Určuje, zda je povolena možnost **výběru inteligentního** odsazení v dialogovém okně **Možnosti.**|
|RequestStockColors|REG_DWORD|0-1|Určuje, zda jsou k barevným klíčovým slovům použity vlastní nebo výchozí barvy.|
|ZobrazitHotURLs|REG_DWORD|0-1|Určuje, zda může uživatel klepnout na adresy URL.|
|Výchozí hodnoty neaktivní adresy URL|REG_DWORD|0-1|Určuje počáteční nastavení možnosti **Povolit navigaci pomocí adresy URL jediným kliknutím** v dialogovém okně **Možnosti.**|
|Výchozí vložení prostoru|REG_DWORD|0-1|Určuje, zda má služba jazyka jako výchozí možnost karty možnost Vložit mezery.|
|Možnost Zobrazit dropdownbarOption|REG_DWORD|0-1|Povolí nebo zakáže možnost **Navigační pruh** v dialogovém okně **Možnosti,** které zobrazuje nebo skryje **navigační panel**.|
|Pouze okno s jedním kódem|REG_DWORD|0-1|Povolí nebo zakáže volbu **Nové okno** v nabídce **Okno** pro jazykovou službu.|
|EnableAdvancedMembersOption|REG_DWORD|0-1|Povolí nebo zakáže nastavení dialogového okna **Možnosti** pro **skrýt rozšířené členy**.|
|Podpora CF_HTML|REG_DWORD|0-1|Určuje, zda editor povolí kopírování a vkládání dat HTML.|
|EnableLineNumbersOption|REG_DWORD|0-1|Určuje, zda jsou pro jazykovou službu povoleny možnosti **Čísla řádků** v dialogovém okně **Možnosti.**|
|HideAdvancedMembersByDefault|REG_DWORD|0-1|Určuje, zda jsou rozšířené členy, například soukromá pole, skryty v seznamech dokončení.|
|Zobrazitdokončení rovnátka|REG_DWORD|0-1|Určuje, zda je povolena možnost **dokončení závorky** v dialogovém okně **Možnosti.**|

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

## <a name="registry-entries-for-debugger-languages-options"></a>Položky registru pro možnosti ladicích jazyků
 *Kořenový adresář VS*\Languages\Language Services\\Název\\*jazyka*\Název*jazyka*Ladicí jazyk \ klíč může obsahovat následující hodnoty.

|Name (Název)|Typ|Rozsah|Popis|
|----------|----------|-----------|-----------------|
|(Výchozí)|REG_SZ|text|Výchozí hodnotu lze použít k dokumentaci názvu jazyka. Název tohoto klíče je identifikátor GUID vyhodnocení výrazu, který má odpovídající položku v * \<Kořenovém>* \AD7Metrics\Expression Evaluator.|

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
 Klíče registru můžete přidat pod klíčem EditorToolsOptions pro stránky vlastností a uzly vlastností. Tyto klávesy a jejich hodnoty identifikují stránky vlastností v dialogovém okně **Možnosti** (v nabídce **Nástroje),** které se používají ke konfiguraci jazykové služby. V následujícím příkladu je *název stránky stránky vlastností* a *název uzlu* ve stromu v dialogovém okně **Možnosti.** Položka stránky a položka uzlu musí být zadány samostatně.

|Name (Název)|Typ|Rozsah|Popis|
|----------|----------|-----------|-----------------|
|(Výchozí)|REG_SZ|Resid|Lokalizovaný zobrazovaný název této stránky možností. Název může být literál`nnn`text, `nnn` nebo # , kde je id řetězce prostředku v satelitní DLL zadaného VSPackage.|
|Balíček|REG_SZ|*Identifikátor guid*|Guid v Balíčku VSPackage, který implementuje tuto stránku možností.|
|stránka|REG_SZ|*Identifikátor guid*|GUID stránky vlastností požadovat z VSPackage voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> metody. Pokud tato položka registru není k dispozici, klíč registru popisuje uzel, nikoli stránku.|

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

## <a name="registry-entries-for-file-name-extension-options"></a>Položky registru pro možnosti rozšíření názvu souboru
 Položka pro příponu souboru by měla obsahovat úvodní období, například ".myext".

|Name (Název)|Typ|Rozsah|Popis|
|----------|----------|-----------|-----------------|
|(Výchozí)|REG_SZ|*Identifikátor guid*|Identifikátor GUID služby pro výchozí jazykovou službu pro tento typ přípony názvu souboru.|

### <a name="example"></a>Příklad

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\
  Languages\
    File Extensions\
      .cpp\
        (Default) = {B2F072B0-ABC1-11D0-9D62-00C04FD9DFD9}
```

## <a name="registry-entries-for-editor-options"></a>Položky registru pro možnosti editoru
 Klíč *Kořenový adresář*Editory VS může obsahovat následující hodnoty:

|Name (Název)|Typ|Rozsah|Popis|
|----------|----------|-----------|-----------------|
|(Výchozí)|REG_SZ|""|Nevyužito; můžete dát své jméno zde pro dokumentaci.|
|Výchozí panel nástrojů|REG_SZ|""|Název karty panelu nástrojů, aby se výchozí, když editor je aktivní.|
|DisplayName|REG_SZ|Resid|Název, který se zobrazí v dialogovém okně **Otevřít v písmenu A.** Název je ID prostředků řetězce nebo název ve standardním formátu.|
|ExcludeDefTextEditor|REG_DWORD|0-1|Používá se pro příkaz **Nabídky Otevřít s.** Pokud nechcete v seznamu dostupných editorů pro určitý typ souboru uvést výchozí textový editor, nastavte tuto hodnotu na hodnotu 1.|
|LinkedEditorGUID|REG_SZ|*\<>IDENTIFIKÁTORGUID*|Používá se pro všechny jazykové služby, které mohou otevřít soubor s podporou znakové stránky. Pokud například otevřete soubor TXT pomocí příkazu **Otevřít pomocí,** jsou k dispozici možnosti pro použití editoru zdrojového kódu s kódováním a bez něj.<br /><br /> Identifikátor GUID zadaný v názvu podklíče je určen pro továrnu editoru znakových stránek. propojený identifikátor GUID zadaný v této konkrétní položce registru je určen pro běžnou továrnu editoru. Účelem této položky je, že pokud rozhraní IDE neotevře soubor pomocí výchozího editoru, ide se pokusí použít další editor v seznamu. Tento další editor by neměl být factory editor usměrovací stránky, protože tento editor factory je v podstatě stejný jako editor factory, který selhal.|
|Balíček|REG_SZ|*\<>IDENTIFIKÁTORGUID*|Identifikátor GUID vspackage pro identifikátor ResID zobrazované hosti.|

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
 Klíč *Gui editoru editoru editoru VS*\\*\ editorů>* \LogicalViews může obsahovat následující hodnoty.

|Name (Název)|Typ|Rozsah|Popis|
|----------|----------|-----------|-----------------|
|(Výchozí)|REG_SZ||Nepoužívá se.|
|*\<>IDENTIFIKÁTORGUID*|REG_SZ|""|Klíč k podporovaným logickým zobrazením. Můžete jich mít tolik, kolik potřebujete. Název položky registru je to, co je důležité, nikoli hodnota, která je vždy prázdný řetězec.|

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
 Klíč\\*GUID \Rozšíření editoru* *vs Reg*může obsahovat následující hodnoty. Přípona názvu souboru neobsahuje úvodní tečku.

|Name (Název)|Typ|Rozsah|Popis|
|----------|----------|-----------|-----------------|
|(Výchozí)|REG_SZ||Nepoužívá se.|
|*\<ext>*|REG_DWORD|0-0xffffffffffffff|Relativní priorita rozšíření. Pokud dva nebo více jazyků sdílejí stejné rozšíření, zvolí se jazyk s vyšší prioritou.|

 Výchozí výběr aktuálního\\uživatele pro editor je navíc uložen v HKEY_Current_User\Software\Microsoft\Microsoft\VisualStudio\\*X.Y*\Default Editors*ext*. Identifikátor GUID vybrané jazykové služby je v položce Vlastní. To má přednost pro aktuálního uživatele.

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

## <a name="registry-entries-for-managed-package-framework-language-service-options"></a>Položky registru pro možnosti služby Language Language Language sady Spravovaného balíčku
 Následující položky registru jsou specifické pro třídy jazykových služeb architektury spravovaného balíčku (MPF). Tyto položky registru označují podporu v jazykové službě pro různé funkce Technologie IntelliSense a pro další pokročilé funkce úprav.

 Tyto položky registru jsou <xref:Microsoft.VisualStudio.Package.LanguagePreferences> přístupné prostřednictvím třídy.

|Name (Název)|Typ|Rozsah|Popis|
|----------|----------|-----------|-----------------|
|CodeSense|REG_DWORD|0-1|Podpora operací IntelliSense.|
|MatchBraces|REG_DWORD|0-1|Podpora odpovídajících jazykových párů, jako jsou závorky, závorky a závorky.|
|Rychlé informace|REG_DWORD|0-1|Podpora operace IntelliSense Quick Info.|
|Zobrazitodpovídajícírovná|REG_DWORD|0-1|Podpora pro zobrazení odpovídající hojazyka dvojice ve stavovém řádku.|
|MatchBracesAtCaret|REG_DWORD|0-1|Podpora pro zobrazení odpovídající jazykové dvojice, obvykle prostřednictvím zvýraznění dvou prvků.|
|Zprávy maxerror|REG_DWORD|0-n|Maximální počet chyb, které lze zobrazit v okně **Seznam chyb.**|
|CodeSenseDelay|REG_DWORD|0-n|Počet milisekund zpoždění před zahájením jakékoli analýzy na pozadí pro operaci IntelliSense.|
|EnableAsyncCompletion|REG_DWORD|0-1|Podpora analýzy na pozadí.|
|Povolitkomentování|REG_DWORD|0-1|Podpora pro komentování vybraných bloků textu a také zahrnuje podporu pro odkomentování vybraného textu.|
|EnableFormatSelection|REG_DWORD|0-1|Podpora formátování textu, jako je automatické odsazení nebo úprava polohy závorek.|
|Automatické vyztažování|REG_DWORD|0-1|Podpora pro osnovu (oblasti, které lze sbalit).|
|Maximální počet oblastí|REG_DWORD|0-n|Maximální počet skrytých oblastí na soubor.|

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

## <a name="see-also"></a>Viz také
- [Vývoj služby starší verze jazyka](../../extensibility/internals/developing-a-legacy-language-service.md)
