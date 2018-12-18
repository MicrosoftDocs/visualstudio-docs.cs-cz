---
title: Návrhář manifestů VSIX | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.Sdk.VsixManifestEditor
helpviewer_keywords:
- vsixmanifest
- vsix manifest
- manifest designer
ms.assetid: 5a691e77-cf91-430d-90ea-361d9031ef83
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 72639c3fbef6b8e297d9e81a7383b2ee8220d896
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51796438"
---
# <a name="vsix-manifest-designer"></a>Návrhář manifestu VSIX
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Upraví soubor manifestu balíčku VSIX, který nastaví chování při instalaci rozšíření sady Visual Studio.  
  
 **Návrhář manifestu VSIX** mapuje na základní schéma VSIX. Každý prvek ve schématu můžete nastavit pomocí odpovídající ovládací prvek v návrháři. Další informace o schématu najdete v tématu [VSIX Extension Schema 2.0 referenční informace](../extensibility/vsix-extension-schema-2-0-reference.md).  
  
 Chcete-li otevřít **Návrhář manifestu VSIX**, vyhledejte soubor source.extension.vsixmanifest v **Průzkumníka řešení**a otevřete soubor. Pokud soubor neobsahuje platný kód XML, manifest designer nelze otevřít.  
  
> [!NOTE]
>  Source.extension.vsixmanifest se výstup extension.vsixmanifest při vytváření balíčku.  
  
## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní  
 **Návrhář manifestu VSIX** obsahuje čtyři oddíly, které odpovídají těmto nejvyšší úrovně prvky schématu:  
  
- Metadata  
  
- Cíle instalace  
  
- Prostředky  
  
- Závislosti  
  
  Oblast záhlaví obsahuje následující ovládací prvky.  
  
  **Název produktu**  
  Popisuje název rozšíření.  
  
  **ID produktu**  
  Určuje jedinečné identifikační informace pro tento balíček.  
  
  **Autor**  
  Určuje jméno autora rozšíření.  
  
  **Verze**  
  Určuje číslo verze rozšíření.  
  
  **Metadat** karta obsahuje následující ovládací prvky.  
  
  **Popis**  
  Poskytuje textový popis rozšíření, který se má zobrazit v **Správce rozšíření**.  
  
  **Jazyk**  
  Určuje výchozí jazyk pro balíček, který odpovídá textová data v manifestu. `Language` Atribut konvenci, common language runtime (CLR) národního prostředí kódu pro sestavení prostředků, třeba cs-us, en, fr-fr. Výchozí hodnota je neutrální; To znamená, že balíček spustí v jakékoli jazykové verzi sady Visual Studio.  
  
  **Licence**  
  Určuje textový soubor, který obsahuje licenci, pokud je k dispozici.  
  
  **Ikona**  
  Určuje soubor grafiky (.png, .bmp, .jpeg, ICO), který obsahuje ikonu, který se má zobrazit v **Správce rozšíření**, pokud je k dispozici ikona. Obrázek ikony musí být 32 x 32 pixelů nebo se změněnou velikostí do příslušných dimenzí. Pokud není zadána žádná ikona, **Správce rozšíření** používá výchozí ikona.  
  
  **Image ve verzi Preview**  
  Určuje soubor grafiky (.png, .bmp, .jpeg, ICO), který obsahuje obrázek náhledu, který se má zobrazit v **Správce rozšíření**, pokud image ve verzi preview je k dispozici. Obrázek náhledu, musí být 200 x 200 pixelů. Pokud není zadán žádný náhled obrázku, **Správce rozšíření** používá výchozí image.  
  
  **Značky**  
  Přidá text značky pro tipy pro hledání.  
  
  **Zpráva k vydání verze**  
  Určuje soubor (.txt, RTF), který obsahuje zprávu k vydání verze. Přijímá také adresu URL webu, který se zobrazí zpráva k vydání verze.  
  
  **Příručka Začínáme**  
  Určuje soubor (.txt, RTF), který obsahuje informace o tom, jak použít rozšíření nebo obsah v balíčku souboru VSIX. Tento průvodce se zobrazí po dokončení instalace rozšíření. Přijímá také adresu URL webu, který se zobrazí v průvodci.  
  
  **Další informace o adrese URL**  
  Určuje adresu URL webu, který obsahuje další informace o produktu.  
  
  **Cíle instalace** karta obsahuje následující ovládací prvky.  
  
  **Typ instalace**  
  Obsahuje seznam **rozšíření sady Visual Studio** a **rozšíření SDK** tak, jak cílit na typech instalace. Možnosti se liší v závislosti na typu, který zvolíte.  
  
  **Rozšíření sady Visual Studio**  
  Obsahuje seznam **InstallationTarget** prvky, které popisují, jak lze nainstalovat balíček a do které produkty sady Visual Studio můžou toto rozšíření nainstalovat. Každý produkt se identifikují samostatně, lepší výkon díky název a verzi nebo verzi.  Produkty lze přidávat do seznamu, upravit a odstranit. Název a verzi produktu odpovídá **Id** a **verze** atributy přidruženého **InstallationTarget** elementu.  
  
  **Rozsah verzí** je [12,0, 14,0] a používá následující zápis:  
  
- [– minimální verze (včetně)  
  
- ] – maximální verze (včetně)  
  
- (– minimální verze exkluzivní  
  
- ) – exkluzivní maximální verze  
  
- Jedna verze # - jenom určená verze  
  
  **Rozšíření sady SDK**  
  Určuje globální instalace, který není v oboru konkrétního produktu a verze. **Identifikátor cílové platformy** je na platformě, jako je například "Windows,", který cílíte. **Cílit na verzi platformy** je verze, jako je například 8.0 cílové platformy. **Název sady SDK** a **verze sady SDK** jsou název a číslo verze sady SDK, v uvedeném pořadí.  
  
  **Tento VSIX se nainstalují pro všechny uživatele (vyžaduje zvýšení úrovně oprávnění při instalaci)** zaškrtávací políčko  
  Pokud je toto políčko zaškrtnuto, toto rozšíření je nainstalované pro všechny uživatele; v opačném případě se nainstaluje pouze pro aktuálního uživatele.  
  
  **Tento VSIX nainstalovaného pomocí Instalační služby systému Windows** zaškrtávací políčko  
  Pokud je toto políčko zaškrtnuto, toto rozšíření je nainstalováno pomocí Instalační služby systému Windows (soubor .msi); v opačném případě je nainstalována jako typického balíčku VSIX (soubor .vsix).  
  
  **Prostředky** karta obsahuje následující ovládací prvky.  
  
  **Seznam prostředků**  
  Obsahuje seznam prvků Assetu, které popisují prvky rozšíření nebo obsahu, že tento balíček zařízení surface. Každé rozšíření nebo obsahu elementu je uvedena samostatně podle zdroje, typu a cestu. Prvky rozšíření a obsah můžete přidat do seznamu, upravit a odstranit. Typ a cestu k rozšíření nebo obsah elementu odpovídá `Type` a `Path` atributy přidruženého `Asset` elementu. Jsou známé následující typy:  
  
- Microsoft.VisualStudio.Package  
  
- Microsoft.VisualStudio.MefComponent  
  
- Microsoft.VisualStudio.ToolboxControl  
  
- Microsoft.VisualStudio.Samples  
  
- Microsoft.VisualStudio.ProjectTemplate  
  
- Microsoft.VisualStudio.ItemTemplate  
  
- Microsoft.VisualStudio.Assembly  
  
- Microsoft.ExtensionSDK  
  
  Můžete přidat nebo upravit assetu, musíte zadat typ prostředku, jestli prostředek je projekt v aktuálním řešení nebo soubor v systému souborů a název projektu. Můžete také zadat název složky, ve kterém mají být vloženy.  
  
  Můžete také vytvořit vlastní typy a poskytnout je jedinečné názvy.  
  
  **Závislosti** karta obsahuje následující ovládací prvky.  
  
  **Název zdroje a rozsah verzí**  
  Obsahuje elementy Dependency tohoto balíčku, které jsou i další balíčky, na kterých závisí tento balíček. Pokud je zadaná závislost balíčku, musí být nainstalována před instalací tohoto balíčku; v opačném případě tento balíček musíte jej nainstalovat.  
  
  Závislé balíčky jsou určena podle identifikátoru, název, rozsah verzí, zdroje a jak se závislost, které je potřeba vyřešit. Každý balíček závislostí uvedený samostatně podle názvu, verze a zdroje. Závislé balíčky lze přidávat do seznamu, upravit a odstranit.  
  
  Identifikátor musí odpovídat `ID` atribut metadata balíčků závislostí. Zdrojem může být projekt v aktuálním řešení, aktuálně nainstalovaná rozšíření nebo soubor. **Jak je vyřešit závislost** nastavení může být relativní cesta vnořené balíčku nebo adresu URL umístění stahování pro závislost. ID, verze a řešení závislostí balíčku odpovídají `Id`, `Version`, a `Location` atributy přidruženého `Dependency` elementu.  
  
## <a name="see-also"></a>Viz také  
 [VSIX Extension Schema 2.0 – referenční informace](../extensibility/vsix-extension-schema-2-0-reference.md)   
 [Anatomie balíčku VSIX](../extensibility/anatomy-of-a-vsix-package.md)

