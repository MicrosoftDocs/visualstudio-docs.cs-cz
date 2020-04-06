---
title: VSIX Manifest Designer | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VS.Sdk.VsixManifestEditor
helpviewer_keywords:
- vsixmanifest
- vsix manifest
- manifest designer
ms.assetid: 5a691e77-cf91-430d-90ea-361d9031ef83
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 30620e0fe91d0e90995d2d2f721950f878c65fdc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697897"
---
# <a name="vsix-manifest-designer"></a>Návrhář manifestu VSIX
Upraví soubor manifestu balíčku VSIX, který nastaví chování instalace pro rozšíření sady Visual Studio.

 **VSIX Manifest Designer** mapuje na základní schéma VSIX. Každý prvek ve schématu lze nastavit pomocí odpovídající ovládací prvek v návrháři. Další informace o schématu naleznete v tématu [VSIX Extension Schema 2.0 Reference](../extensibility/vsix-extension-schema-2-0-reference.md).

 Chcete-li otevřít **Návrhář manifestu VSIX**, vyhledejte soubor *source.extension.vsixmanifest* v **Průzkumníku řešení**a otevřete soubor. Pokud soubor neobsahuje platný kód XML, návrhář manifestu se neotevře.

> [!NOTE]
> Soubor *source.extension.vsixmanifest* je výstup na *extension.vsixmanifest* při sestavení balíčku.

## <a name="uielement-list"></a>Seznam Prvků UI
 **Návrhář manifestu VSIX** obsahuje čtyři oddíly, které odpovídají těmto prvkům nejvyšší úrovně schématu:

- Metadata

- Instalace cílů

- Prostředky

- Závislosti

  Oblast nadpisu obsahuje následující ovládací prvky.

  **Název produktu** Popisuje název rozšíření.

  **ID produktu** Určuje jedinečné identifikační informace pro tento balíček.

  **Autor** Určuje jméno autora rozšíření.

  **Verze** Určuje číslo verze rozšíření.

  Karta **Metadata** obsahuje následující ovládací prvky.

  **Popis** Obsahuje textový popis rozšíření, které se zobrazí ve **Správci rozšíření**.

  **Jazyk** Určuje výchozí jazyk pro balíček, který odpovídá textovým datům v manifestu. Atribut `Language` následuje konvence kódu národního prostředí cltime společného jazyka (CLR) pro sestavení prostředků, například en-us, en, fr-fr. Ve výchozím nastavení je hodnota neutrální, což znamená, že balíček bude spuštěn v libovolné jazykové verzi sady Visual Studio.

  **Licence** Určuje textový soubor, který obsahuje uživatelskou licenci, pokud je k dispozici.

  **Ikona** Určuje grafický soubor (*.png*, *.bmp*, *.jpeg*, *.ico*), který obsahuje ikonu, která má být zobrazena ve **Správci rozšíření**, pokud je ikona přítomna. Obrázek ikony musí mít rozměr y 32 x 32 pixelů, jinak se jeho velikost na tyto rozměry zmenšuje. Pokud není zadána žádná ikona, **správce rozšíření** použije výchozí ikonu.

  **Náhled obrázku** Určuje grafický soubor (*.png*, *.bmp*, *.jpeg*, *.ico*), který obsahuje náhled obrazu, který má být zobrazen ve **Správci rozšíření**, pokud je k dispozici náhled obrazu. Náhled obrazu musí mít 200 x 200 pixelů. Pokud není zadán žádný náhled obrazu, **Správce rozšíření** používá výchozí obraz.

  **Značky** Přidá textové značky, které se mají použít pro rady při hledání.

  **Poznámky k verzi** Určuje soubor (*.txt*, *.rtf*), který obsahuje poznámky k verzi. Také přebírá adresu URL webu, který zobrazuje poznámky k verzi.

  **Příručka Začínáme** Určuje soubor (*.txt*, *.rtf*), který obsahuje informace o použití přípony nebo obsahu v balíčku VSIX. Tato příručka se zobrazí po dokončení instalace rozšíření. Také přebírá adresu URL webu, který zobrazuje průvodce.

  **Další adresa URL informací** Určuje adresu URL webu, který obsahuje další informace o produktu.

  Karta **Cíle instalace** obsahuje následující ovládací prvky.

  **Typ instalace** Zobrazí seznam **rozšíření sady Visual Studio** a sady **SDK** jako cílové typy instalace. Možnosti se liší v závislosti na zvoleném typu.

  **Rozšíření sady Visual Studio** Uvádí **installationtarget** prvky, které popisují, jak lze nainstalovat balíček a do kterých produktů sady Visual Studio toto rozšíření lze nainstalovat. Každý produkt je identifikován samostatně podle názvu a rozsahu verzí nebo verzí. Produkty lze přidat do seznamu, upravit a odstranit. Název a verze produktu odpovídají **Id** a **Version** atributy přidružené **installationtarget** element.

  **Rozsah verzí** je [12.0, 14.0] a používá následující zápis:

- [ - minimální verze včetně

- ] - maximální verze včetně

- ( - minimální verze exkluzivní

- ) - maximální verze exkluzivní

- Jedna verze # - pouze zadaná verze

  **Sada SDK rozšíření** Určuje globální instalaci, která není vymezena na konkrétní produkt a verzi. **Identifikátor cílové platformy** je platforma, například Windows, na kterou cílíte. **Verze cílové platformy** je verze, například 8.0, cílové platformy. **Název sady SDK** a **verze sady SDK** jsou název a číslo verze sady SDK.

  **Tento VSIX je nainstalován pro všechny uživatele (vyžaduje zvýšení při instalaci)** Pokud zaškrtnete toto políčko, rozšíření je nainstalováno pro všechny uživatele. v opačném případě je nainstalován pouze pro aktuálního uživatele.

  **Tento VSIX je nainstalován Instalační službou systému Windows** Pokud toto políčko zaškrtnete, bude přípona nainstalována Instalační službou systému Windows (*soubor MSI);* v opačném případě je nainstalován jako typický balíček VSIX (*soubor .vsix).*

  Karta **Prostředky** obsahuje následující ovládací prvky.

  **Seznam aktiv** Zobrazí seznam prvků Asset, které popisují prvky rozšíření nebo obsahu, které tento balíček zobrazí. Každý prvek rozšíření nebo obsahu je uveden samostatně podle zdroje, typu a cesty. Rozšíření a prvky obsahu lze přidat do seznamu, upravit a odstranit. Typ a cesta prvku rozšíření nebo obsahu `Type` odpovídá `Path` atributům a `Asset` přidruženého prvku. Následující typy jsou známy:

- Balíček Microsoft.VisualStudio.Package

- Součást Microsoft.VisualStudio.MefComponent

- Ovládací prvek Microsoft.VisualStudio.Toolbox

- Microsoft.VisualStudio.Samples

- Šablona Microsoft.VisualStudio.ProjectTemplate

- Šablona Microsoft.VisualStudio.Item

- Microsoft.VisualStudio.Assembly

- Microsoft.ExtensionSDK

  Chcete-li přidat nebo upravit datový zdroj, musíte zadat typ datového zdroje, zda se jedná o projekt v aktuálním řešení nebo soubor v systému souborů, a název projektu. Můžete také zadat název složky, do které chcete vložit.

  Můžete také vytvořit vlastní typy a dát jim jedinečné názvy.

  Karta **Závislosti** obsahuje následující ovládací prvky.

  **Název, zdroj a rozsah verzí** Seznam prvků závislostí tohoto balíčku, které jsou další balíčky, které tento balíček závisí na. Pokud je zadán balíček závislostí, musí být nainstalován před instalací tohoto balíčku; v opačném případě jej tento balíček musí nainstalovat.

  Balíčky závislostí jsou určeny identifikátorem, názvem, rozsahem verze, zdrojem a způsobem, jakým má být závislost vyřešena. Každý balíček závislostí je uveden samostatně podle názvu, verze a zdroje. Balíčky závislostí lze přidat do seznamu, upravit a odstranit.

  Identifikátor musí odpovídat `ID` atributu metadat balíčku závislostí. Zdrojem může být projekt v aktuálním řešení, aktuálně nainstalované rozšíření nebo soubor. **Jak je závislost vyřešena** nastavení může být relativní cestu vnořený balíček nebo URL umístění pro stahování pro závislost. ID, verze a řešení balíčku závislostí `Id`odpovídají atributům `Version`, `Location` a atributům `Dependency` přidruženého prvku.

## <a name="see-also"></a>Viz také
- [Odkaz na schéma rozšíření VSIX 2.0](../extensibility/vsix-extension-schema-2-0-reference.md)
- [Anatomie balíčku VSIX](../extensibility/anatomy-of-a-vsix-package.md)
