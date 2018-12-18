---
title: Registrace starší verze jazyka2 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- registration, language services
- language services, registry information
- registry, language services
ms.assetid: ca312aa3-f9f1-4572-8553-89bf3a724deb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f247a510b6fb52903970e408f930b13a8faba08e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49879003"
---
# <a name="registering-a-legacy-language-service"></a>Registrace služby starší verze jazyka
Následující části obsahují seznam položky registru pro různé jazykové služby možnostech dostupných v [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 V následujícím seznamu položky registru *VS Reg kořenové* rovná HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*X.Y*, kde *X.Y* je [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] číslo verze.  
  
## <a name="registry-entries-for-language-service-options"></a>Položky registru pro možnosti služby jazyka  
 *VS Reg kořenové*\Languages\Language služby\\*název jazyka* klíč může obsahovat následující hodnoty.  
  
|Název|Typ|Rozsah|Popis|  
|----------|----------|-----------|-----------------|  
|(Výchozí)|REG_SZ|*\<IDENTIFIKÁTOR GUID &GT;*|Identifikátor GUID služby jazyka.|  
|LangResID|REG_DWORD|0x0 0xffff|Řetězec resource identifier (ResID) název základního textu jazyka.|  
|Balíček|REG_SZ|*\<IDENTIFIKÁTOR GUID &GT;*|Identifikátor GUID sady VSPackage.|  
|ShowCompletion|REG_DWORD|0-1|Určuje, zda **dokončování** možnosti v **možnosti** dialogové okno jsou povolené.|  
|ShowSmartIndent|REG_DWORD|0-1|Určuje, zda možnost vybrat si **inteligentní** odsazování v **možnosti** dialogové okno je povolená.|  
|RequestStockColors|REG_DWORD|0-1|Určuje, zda vlastní nebo výchozí barvy se používají k barva klíčová slova.|  
|ShowHotURLs|REG_DWORD|0-1|Určuje, zda může uživatel kliknout adresy URL.|  
|Ve výchozím nastavení není výměně adresy URL|REG_DWORD|0-1|Určuje počáteční nastavení **povolit navigaci adres URL jedním kliknutím** možnost **možnosti** dialogové okno.|  
|DefaultToInsertSpaces|REG_DWORD|0-1|Určuje, zda má služba jazyka "vložení mezer" jako jeho výchozí kartu možnost.|  
|ShowDropdownBarOption|REG_DWORD|0-1|Povolí nebo zakáže **navigační panel** možnost **možnosti** dialogové okno, které zobrazí nebo skryje **navigační panel**.|  
|Pouze jeden kód okno|REG_DWORD|0-1|Povolí nebo zakáže **nové okno** voleb v **okno** nabídku služby jazyka.|  
|EnableAdvancedMembersOption|REG_DWORD|0-1|Povolí nebo zakáže **možnosti** dialogové okno Nastavení pole **Skrýt rozšířené členy**.|  
|Podpora CF_HTML|REG_DWORD|0-1|Určuje, zda editor umožňuje kopírování a vkládání dat ve formátu HTML.|  
|EnableLineNumbersOption|REG_DWORD|0-1|Určuje, zda **čísla řádků** možnosti **možnosti** dialogové okno zapnutá služba jazyka.|  
|HideAdvancedMembersByDefault|REG_DWORD|0-1|Určuje, zda jsou skryté členy rozšířené úrovně, jako je například privátní pole do seznamů dokončení.|  
|ShowBraceCompletion|REG_DWORD|0-1|Určuje, zda **složených závorek dokončení** možnost **možnosti** dialogové okno je povolená.|  
  
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
  
## <a name="registry-entries-for-debugger-languages-options"></a>Položky registru pro jazyky možnosti ladicího programu  
 *VS Reg kořenové*\Languages\Language služby\\*název jazyka*\Debugger jazyky\\*GUID*\ klíč může obsahovat následující hodnoty.  
  
|Název|Typ|Rozsah|Popis|  
|----------|----------|-----------|-----------------|  
|(Výchozí)|REG_SZ|text|Výchozí hodnota je možné na název jazyku dokumentu. Název tohoto klíče je identifikátor GUID vyhodnocovače výrazů, který nemá odpovídající záznam v  *\<VS Reg Root >* \AD7Metrics\Expression Chyba při vyhodnocování.|  
  
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
 Můžete přidat klíče registru pod klíčem EditorToolsOptions stránky vlastností a vlastností uzly. Tyto klíče a jejich hodnoty identifikace stránky vlastností v **možnosti** dialogové okno (na **nástroje** nabídek), která se používají ke konfiguraci služby jazyka. V následujícím příkladu *název stránky* je název stránky vlastností a *název uzlu* je název uzlu ve stromu na **možnosti** dialogové okno. Položky stránky a uzel musí být zadávají samostatně.  
  
|Název|Typ|Rozsah|Popis|  
|----------|----------|-----------|-----------------|  
|(Výchozí)|REG_SZ|resID|Lokalizovaný zobrazovaný název této stránce možnost. Název může obsahovat prostý text nebo #`nnn`, kde `nnn` je řetězec ID prostředku v satelitní knihovně DLL ze zadaného balíčku VSPackage.|  
|Balíček|REG_SZ|*GUID*|Identifikátor GUID sady VSPackage, která implementuje Tato stránka možností.|  
|Stránka|REG_SZ|*GUID*|Identifikátor GUID stránky vlastností k vyžádání ze sady VSPackage pomocí volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> metody. Pokud se tato položka registru není k dispozici, klíče registru popisuje uzlu, nikoli stránku.|  
  
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
  
## <a name="registry-entries-for-file-name-extension-options"></a>Položky registru pro rozšíření možností názvu souboru  
 Položka pro příponu souboru by měla obsahovat úvodní tečku, například ".myext".  
  
|Název|Typ|Rozsah|Popis|  
|----------|----------|-----------|-----------------|  
|(Výchozí)|REG_SZ|*GUID*|Identifikátor GUID služby pro službu výchozí jazyk pro tento typ rozšíření názvu souboru.|  
  
### <a name="example"></a>Příklad  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  Languages\  
    File Extensions\  
      .cpp\  
        (Default) = {B2F072B0-ABC1-11D0-9D62-00C04FD9DFD9}  
```  
  
## <a name="registry-entries-for-editor-options"></a>Položky registru pro možnosti editoru  
 *VS Reg kořenové*\Editors klíč může obsahovat následující hodnoty:  
  
|Název|Typ|Rozsah|Popis|  
|----------|----------|-----------|-----------------|  
|(Výchozí)|REG_SZ|""|NEPOUŽITÝ; můžete vložit sem patří vaše jméno dokumentaci.|  
|DefaultToolboxTab|REG_SZ|""|Název na kartě panelu nástrojů při aktivním editoru nastavit jako výchozí.|  
|displayName|REG_SZ|resID|Název má být zobrazen v **otevřít v** dialogové okno. Název je ID prostředku řetězce nebo názvu ve standardním formátu.|  
|ExcludeDefTextEditor|REG_DWORD|0-1|Používá pro **otevřít v** příkazu nabídky. Pokud nechcete seznamu textový editor výchozí seznam dostupných editorů pro určitý typ souboru, nastavte tuto hodnotu na 1.|  
|LinkedEditorGUID|REG_SZ|*\<IDENTIFIKÁTOR GUID &GT;*|Použít pro jakékoli službě jazyka, který můžete otevřít soubor s podporou znakovou stránku. Například, když otevřete soubor s příponou .txt pomocí **otevřít v programu** příkazu, možnosti jsou k dispozici pro použití editoru zdrojového kódu s a bez kódování.<br /><br /> Je zadaný název podklíče identifikátor GUID objektu pro vytváření editoru znakovou stránku, která; propojené identifikátor GUID specifikovaný v konkrétním registru je pro objekt pro vytváření editoru regulárních. Účelem této položky je, že pokud integrovaného vývojového prostředí pomocí výchozího editoru soubor neotevře, rozhraní IDE se pokusí použít další editoru v seznamu. Tento dalším editor by neměl být objekt factory editoru znakovou stránku, protože tento objekt pro vytváření editoru je v podstatě stejný jako objekt factory editoru, který selhal.|  
|Balíček|REG_SZ|*\<IDENTIFIKÁTOR GUID &GT;*|Identifikátor GUID balíčku VSPackage pro ResID zobrazovaný název.|  
  
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
  
## <a name="registry-entries-for-logical-view-options"></a>Položky registru pro možnosti logické zobrazení  
 *VS Reg kořenové*\Editors\\*grafické uživatelské rozhraní editoru >* \LogicalViews klíč může obsahovat následující hodnoty.  
  
|Název|Typ|Rozsah|Popis|  
|----------|----------|-----------|-----------------|  
|(Výchozí)|REG_SZ||Nevyužité.|  
|*\<IDENTIFIKÁTOR GUID &GT;*|REG_SZ|""|Klíč k logické zobrazení podporována. Podle potřeby, můžete mít kolik z nich. Název položky registru je, co je důležité, nikoli hodnotu, která je vždy prázdný řetězec.|  
  
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
 *VS Reg kořenové*\Editors\\*identifikátor GUID editoru*\Extensions klíč může obsahovat následující hodnoty. Přípona názvu souboru neobsahuje první pozici tečku.  
  
|Název|Typ|Rozsah|Popis|  
|----------|----------|-----------|-----------------|  
|(Výchozí)|REG_SZ||Nevyužité.|  
|*\<ext, přípona >*|REG_DWORD|0 0xffffffff|Relativní priorita daného rozšíření. Pokud dva nebo více jazyků sdílet stejnou příponu, zvolí se jazyk s vyšší prioritou.|  
  
 Kromě toho je aktuální uživatel výchozí výběr pro editor uložený v HKEY_Current_User\Software\Microsoft\VisualStudio\\*X.Y*\Default editory\\*ext*. Identifikátor GUID služby vybraný jazyk je v položce vlastní. To má přednost před pro aktuálního uživatele.  
  
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
  
## <a name="registry-entries-for-managed-package-framework-language-service-options"></a>Položky registru pro službu Managed Package Framework jazykového  
 Následující položky registru jsou specifické pro třídy služeb jazyka framework (MPF) spravovaného balíčku. Tyto položky registru indikovat podporu ve službě jazyka pro různé funkce technologie IntelliSense a dalších pokročilé funkce pro úpravy.  
  
 Tyto položky registru jsou přístupné prostřednictvím <xref:Microsoft.VisualStudio.Package.LanguagePreferences> třídy.  
  
|Název|Typ|Rozsah|Popis|  
|----------|----------|-----------|-----------------|  
|CodeSense|REG_DWORD|0-1|Podpora pro operace IntelliSense.|  
|MatchBraces|REG_DWORD|0-1|Podpora pro odpovídající dvojice jazyků, jako jsou složené závorky, závorky a hranaté závorky.|  
|Rychlé informace|REG_DWORD|0-1|Podpora pro operaci rychlé informace technologie IntelliSense.|  
|ShowMatchingBrace|REG_DWORD|0-1|Podpora zobrazení shodnou dvojici jazyka ve stavovém řádku.|  
|MatchBracesAtCaret|REG_DWORD|0-1|Podpora zobrazení odpovídající dvojice jazyků, obvykle prostřednictvím zvýraznění dva elementy.|  
|MaxErrorMessages|REG_DWORD|0-n|Maximální počet chyb, které se dají zobrazit v **seznam chyb** okna.|  
|CodeSenseDelay|REG_DWORD|0-n|Počet milisekund pro zpoždění před inicializací jakékoli pozadí analýza kódu pro operace IntelliSense.|  
|EnableAsyncCompletion|REG_DWORD|0-1|Podpora pro analýzu na pozadí.|  
|EnableCommenting|REG_DWORD|0-1|Podpora pro okomentováním odpovídajícího vybrané bloky textu a také zahrnuje podporu pro odstraňuje se komentování vybraného textu.|  
|EnableFormatSelection|REG_DWORD|0-1|Podpora pro formátování textu, jako je například Automatické odsazení nebo nastavení pozice složených závorek.|  
|AutoOutlining|REG_DWORD|0-1|Podpora osnovy (oblasti, které mohou být sbalena).|  
|MaxRegions|REG_DWORD|0-n|Maximální počet skrytých oblastí na soubor.|  
  
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
 [Vývoj služby starší verze jazyka](../../extensibility/internals/developing-a-legacy-language-service.md)