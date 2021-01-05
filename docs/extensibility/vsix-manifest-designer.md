---
title: Návrhář manifestu VSIX | Microsoft Docs
description: Přečtěte si, jak návrhář manifestu VSIX mění soubor manifestu balíčku VSIX, který nastaví chování při instalaci pro rozšíření sady Visual Studio.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 6323b4330279848bc0453bdc7413904e2582d13a
ms.sourcegitcommit: dd96a95d87a039525aac86abe689c30e2073ae87
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/04/2021
ms.locfileid: "97863969"
---
# <a name="vsix-manifest-designer"></a>Návrhář manifestu VSIX
Upraví soubor manifestu balíčku VSIX, který nastaví chování při instalaci pro rozšíření sady Visual Studio.

 **Návrhář manifestu VSIX** se mapuje na základní schéma VSIX. Každý prvek ve schématu lze nastavit pomocí odpovídajícího ovládacího prvku v návrháři. Další informace o schématu najdete v referenčních informacích k [schématu rozšíření VSIX 2,0](../extensibility/vsix-extension-schema-2-0-reference.md).

 Pro otevření **nástroje VSIX manifest Designer** vyhledejte v **Průzkumník řešení** soubor *source. extension. vsixmanifest* a otevřete soubor. Pokud soubor neobsahuje platný kód XML, Návrhář manifestu se neotevře.

> [!NOTE]
> Soubor *source. extension. vsixmanifest* je výstupem do souboru *extension. vsixmanifest* při sestavení balíčku.

## <a name="uielement-list"></a>UIElement – seznam
 **Návrhář manifestu VSIX** obsahuje čtyři části, které odpovídají těmto prvkům nejvyšší úrovně schématu:

- Metadata

- Cíle instalace

- Prostředky

- Závislosti

  Oblast nadpisu obsahuje následující ovládací prvky.

  **Název produktu** Popisuje název rozšíření.

  **ID produktu** Určuje jedinečné identifikační informace pro tento balíček.

  **Autor** Určuje jméno autora rozšíření.

  **Verze** Určuje číslo verze rozšíření.

  Karta **metadata** obsahuje následující ovládací prvky.

  **Popis** Poskytuje textový popis rozšíření, který se má zobrazit ve **Správci rozšíření**.

  **Jazyk** Určuje výchozí jazyk pro balíček, který odpovídá textovým datům v manifestu. `Language`Atribut následuje konvence kódu národního prostředí modulu CLR (Common Language Runtime) pro sestavení prostředků, například en-US, EN, fr-fr. Ve výchozím nastavení je hodnota neutrální, což znamená, že balíček bude spuštěn v libovolné jazykové verzi sady Visual Studio.

  **Licence** Určuje textový soubor, který obsahuje uživatelskou licenci, pokud je k dispozici.

  **Ikona** Určuje soubor grafiky (*. png*, *. bmp*, *. jpeg*, *. ico*), který obsahuje ikonu, která se má zobrazit ve **Správci rozšíření**, pokud je k dispozici ikona. Obrázek ikony musí být 32x32 pixelů nebo se změní jeho velikost na tyto dimenze. Pokud není zadána žádná ikona, **Správce rozšíření** použije výchozí ikonu.

  **Náhled obrázku** Určuje soubor grafiky (*. png*, *. bmp*, *. jpeg*, *. ico*), který obsahuje obrázek náhledu, který se má zobrazit ve **Správci rozšíření**, pokud je k dispozici náhled obrázku. Obrázek náhledu musí být 200x200 pixelů. Pokud není zadán žádný náhled obrázku, **Správce rozšíření** použije výchozí obrázek.

  **Značky** Přidá textové značky, které se použijí pro tipy hledání.

  **Poznámky k verzi** Určuje soubor (*. txt*, *. RTF*), který obsahuje poznámky k verzi. Také převezme adresu URL webu, který zobrazuje poznámky k verzi.

  **Průvodce Začínáme** Určuje soubor (*. txt*, *. RTF*), který obsahuje informace o tom, jak používat rozšíření nebo obsah v balíčku VSIX. Tato příručka se zobrazí po dokončení instalace rozšíření. Také převezme adresu URL webu, který zobrazí průvodce.

  **Adresa URL s dalšími informacemi** Určuje adresu URL webu, který obsahuje další informace o produktu.

  Karta **cíle instalace** obsahuje následující ovládací prvky.

  **Typ instalace** Vypíše **rozšíření sady Visual Studio** a **sadu SDK rozšíření** jako cílové typy instalace. Možnosti se liší v závislosti na zvoleném typu.

  **Rozšíření sady Visual Studio** Obsahuje seznam **InstallationTarget** prvků, které popisují, jak lze balíček nainstalovat a do kterých produktů sady Visual Studio může být toto rozšíření nainstalováno. Každý produkt se identifikuje samostatně podle názvu a verze nebo rozsahu verze. Produkty lze do seznamu přidat, upravit a odstranit. Název a verze produktu odpovídají atributům **ID** a **verze** přidruženého elementu **InstallationTarget** .

  **Rozsah verzí** je [12,0, 14,0] a používá následující zápis:

- [-minimální verze včetně

- ] – maximální verze včetně

- (-minimální verze exkluzivní

- ) – maximální verze exkluzivní

- Jenom jedna verze – jenom zadaná verze

  **Sada SDK rozšíření** Určuje globální instalaci, která není v oboru pro určitý produkt a verzi. **Identifikátor cílové platformy** je platforma, například "Windows", na kterou cílíte. **Verze cílové platformy** je verze, například 8,0, cílové platformy. Název **sady** SDK a **verze sady SDK** jsou název a číslo verze sady SDK v uvedeném pořadí.

  **Tento VSIX je nainstalován pro všechny uživatele (vyžaduje zvýšení oprávnění při instalaci)** . Pokud zaškrtnete toto políčko, rozšíření se nainstaluje pro všechny uživatele. v opačném případě je nainstalována pouze pro aktuálního uživatele.

  **Tento VSIX je nainstalován pomocí Instalační služba systému Windows** Pokud zaškrtnete toto políčko, rozšíření bude nainstalováno Instalační služba systému Windows (soubor *. msi* ); v opačném případě je nainstalována jako typický balíček VSIX (soubor *. vsix* ).

  Karta **assets (prostředky** ) obsahuje následující ovládací prvky.

  **Seznam prostředků** Obsahuje seznam prvků Assetu, které popisují rozšíření nebo prvky obsahu, které tento balíček povrchuje. Každé rozšíření nebo prvek obsahu je uvedeno samostatně podle zdroje, typu a cesty. Rozšíření a prvky obsahu lze přidat do seznamu, upravit a odstranit. Typ a cesta rozšíření nebo elementu obsahu odpovídají `Type` `Path` atributům a přidruženého `Asset` prvku. Jsou známy následující typy:

- Microsoft. VisualStudio. Package

- Microsoft. VisualStudio. MefComponent

- Microsoft. VisualStudio. ToolboxControl

- Microsoft. VisualStudio. Samples

- Microsoft. VisualStudio. ProjectTemplate

- Microsoft. VisualStudio. ItemTemplate

- Microsoft. VisualStudio. Assembly

- Microsoft. ExtensionSDK

  Chcete-li přidat nebo upravit Asset, je nutné zadat typ assetu, zda se jedná o projekt v aktuálním řešení nebo v souboru v systému souborů a název projektu. Můžete také zadat název složky, do které chcete vložit.

  Můžete také vytvořit vlastní typy a dát jim jedinečné názvy.

  Karta **závislosti** obsahuje následující ovládací prvky.

  **Název, zdroj a rozsah verze** Uvádí prvky závislosti tohoto balíčku, na kterých jsou další balíčky, na kterých tento balíček závisí. Pokud je zadaný balíček závislostí, musí být nainstalovaný před instalací tohoto balíčku. v opačném případě musí tento balíček nainstalovat.

  Balíčky závislostí jsou určeny podle identifikátoru, názvu, rozsahu verze, zdroje a způsobu řešení závislosti. Každý balíček závislosti je uveden samostatně podle názvu, verze a zdroje. Balíčky závislostí se dají přidat do seznamu, upravit a odstranit.

  Identifikátor se musí shodovat s `ID` atributem metadat balíčku závislostí. Zdrojem může být projekt v aktuálním řešení, aktuálně nainstalované rozšíření nebo soubor. Nastavení **vyřešené závislosti** může být relativní cesta k vnořenému balíčku nebo adresa URL umístění pro stažení závislosti. ID, verze a rozlišení balíčku závislostí odpovídají `Id` `Version` `Location` atributům, a přidruženého `Dependency` prvku.

## <a name="see-also"></a>Viz také
- [Referenční dokumentace schématu rozšíření VSIX 2,0](../extensibility/vsix-extension-schema-2-0-reference.md)
- [Anatomie balíčku VSIX](../extensibility/anatomy-of-a-vsix-package.md)
