---
title: Návrhář manifestu VSIX | Microsoft Docs
description: Zjistěte, jak Návrhář manifestu VSIX upravuje soubor manifestu balíčku VSIX, který nastavuje chování instalace Visual Studio rozšíření.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.Sdk.VsixManifestEditor
helpviewer_keywords:
- vsixmanifest
- vsix manifest
- manifest designer
ms.assetid: 5a691e77-cf91-430d-90ea-361d9031ef83
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: baea7be60c67f186da2372c4644366b4a1a7a202
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905186"
---
# <a name="vsix-manifest-designer"></a>Návrhář manifestu VSIX
Upraví soubor manifestu balíčku VSIX, který nastaví chování instalace pro Visual Studio rozšíření.

 Návrhář **manifestu VSIX se** mapuje na podkladové schéma VSIX. Každý prvek ve schématu lze nastavit pomocí odpovídajícího ovládacího prvku v návrháři. Další informace o schématu najdete v referenčních informacích k rozšíření [VSIX Schema 2.0.](../extensibility/vsix-extension-schema-2-0-reference.md)

 Pokud chcete otevřít **Návrháře manifestu VSIX,** vyhledejte soubor *source.extension.vsixmanifest* **v Průzkumník řešení** a otevřete soubor . Pokud soubor neobsahuje platný kód XML, návrhář manifestu se neotevře.

> [!NOTE]
> Soubor *source.extension.vsixmanifest* je výstupem *souboru extension.vsixmanifest,* když je balíček sestaven.

## <a name="uielement-list"></a>Seznam UIElement
 Návrhář **manifestu VSIX** obsahuje čtyři oddíly, které odpovídají těmto prvkům nejvyšší úrovně schématu:

- Metadata

- Cíle instalace

- Prostředky

- Závislosti

  Oblast nadpisu obsahuje následující ovládací prvky.

  **Název produktu** Popisuje název rozšíření.

  **ID produktu** Určuje jedinečné identifikační informace pro tento balíček.

  **Autor** Určuje jméno autora rozšíření.

  **Verze** Určuje číslo verze rozšíření.

  Karta **Metadata** obsahuje následující ovládací prvky.

  **Popis** Poskytuje textový popis rozšíření, který se zobrazí ve **Správci rozšíření.**

  **Jazyk** Určuje výchozí jazyk balíčku, který odpovídá textovým datům v manifestu. Atribut se řídí konvencí kódu národního prostředí clr (Common Language Runtime) pro sestavení prostředků, například `Language` en-us, en, fr-fr. Ve výchozím nastavení je hodnota neutrální, což znamená, že balíček bude spuštěn v libovolné jazykové verzi Visual Studio.

  **Licence** Určuje textový soubor, který obsahuje uživatelskou licenci, pokud existuje.

  **Ikona** Určuje grafický soubor (*.png*, *.bmp*, *.jpeg*, *.ico*), který obsahuje ikonu, která se má zobrazit ve Správci rozšíření **,** pokud je k dispozici ikona. Obrázek ikony musí mít velikost 32 × 32 pixelů nebo se změní na tyto rozměry. Pokud není zadaná žádná ikona, **Správce rozšíření** použije výchozí ikonu.

  **Obrázek náhledu** Určuje grafický soubor (*.png*, *.bmp*, *.jpeg*, *.ico*), který obsahuje náhled obrázku, který se má zobrazit ve **Správci** rozšíření, pokud je k dispozici obrázek náhledu. Náhled obrázku musí být 200 × 200 pixelů. Pokud není zadaná žádná image ve verzi **Preview, Správce rozšíření** použije výchozí image.

  **Značky** Přidá textové značky, které se budou používat pro nápovědy vyhledávání.

  **Poznámky k verzi** Určuje soubor *(*.txt, *.rtf*), který obsahuje poznámky k verzi. Vezme také adresu URL webu, který zobrazuje poznámky k verzi.

  **Začínáme průvodce** Určuje soubor *(*.txt, *.rtf*), který obsahuje informace o použití přípony nebo obsahu v balíčku VSIX. Tato příručka se zobrazí po dokončení instalace rozšíření. Vezme také adresu URL webu, který zobrazuje průvodce.

  **Další informace o adrese URL** Určuje adresu URL webu, který obsahuje další informace o produktu.

  Karta **Cíle instalace** obsahuje následující ovládací prvky.

  **Typ instalace** Uvádí **Visual Studio rozšíření** a rozšíření **SDK** jako cílové typy instalace. Možnosti se liší v závislosti na typu, který zvolíte.

  **Visual Studio rozšíření** Uvádí **elementy InstallationTarget,** které popisují, jak lze balíček nainstalovat a do kterých Visual Studio lze toto rozšíření nainstalovat. Každý produkt je identifikován samostatně podle názvu a verze nebo rozsahu verzí. Produkty je možné přidat do seznamu, upravit a odstranit. Název a verze produktu odpovídají atributům **Id** a **Version** přidruženého **elementu InstallationTarget.**

  **Rozsah verzí** je [12.0, 14.0] a používá následující notaci:

- [ – minimální verze včetně

- ] – maximální verze včetně

- ( – minimální verze se vylučují

- ) – maximální verze (exkluzivní)

- Jedna verze # – pouze zadaná verze

  **Sada SDK rozšíření** Určuje globální instalaci, která není vymezená na konkrétní produkt a verzi. **Identifikátor cílové platformy** je platforma, například Windows, na kterou cílíte. **Verze cílové platformy** je verze cílové platformy, například 8.0. **Název sady** **SDK a verze** sady SDK jsou název a číslo verze sady SDK.

  **Tento soubor VSIX je nainstalovaný pro všechny uživatele (vyžaduje zvýšení oprávnění při instalaci).** Pokud toto políčko zaškrtáte, rozšíření se nainstaluje pro všechny uživatele. Jinak se nainstaluje jenom pro aktuálního uživatele.

  **Tento soubor VSIX instaluje Instalační služba systému Windows** Pokud toto políčko zaškrtáte, rozšíření nainstaluje Instalační služba systému Windows (*.msi* souboru). Jinak se nainstaluje jako typický balíček VSIX (*soubor .vsix).*

  Karta **Assets** (Prostředky) obsahuje následující ovládací prvky.

  **Seznam prostředků** Vypíše prvky assetu, které popisují rozšíření nebo prvky obsahu, které tento balíček zobrazí. Každý prvek rozšíření nebo obsahu je uveden samostatně podle zdroje, typu a cesty. Rozšíření a elementy obsahu je možné přidat do seznamu, upravit a odstranit. Typ a cesta rozšíření nebo elementu obsahu odpovídá atributům a `Type` `Path` přidruženého `Asset` elementu. Jsou známé následující typy:

- Microsoft.VisualStudio.Package

- Microsoft.VisualStudio.MefComponent

- Microsoft.VisualStudio.ToolboxControl

- Microsoft.VisualStudio.Samples

- Microsoft.VisualStudio.ProjectTemplate

- Microsoft.VisualStudio.ItemTemplate

- Microsoft.VisualStudio.Assembly

- Microsoft.ExtensionSDK

  Pokud chcete přidat nebo upravit prostředek, musíte zadat typ assetu, jestli je asset projektem v aktuálním řešení nebo souborem v systému souborů, a název projektu. Můžete také zadat název složky, do které se má vložit.

  Můžete také vytvořit vlastní typy a dát jim jedinečné názvy.

  Karta **Závislosti** obsahuje následující ovládací prvky.

  **Název, zdroj a rozsah verzí** Vypíše elementy závislostí tohoto balíčku, což jsou další balíčky, na kterých tento balíček závisí. Pokud je zadaný balíček závislostí, musí se nainstalovat před jeho nainstalování. Jinak ho tento balíček musí nainstalovat.

  Balíčky závislostí jsou určeny identifikátorem, názvem, rozsahem verzí, zdrojem a způsobem, jakým se má závislost vyřešit. Každý balíček závislostí je uvedený samostatně podle názvu, verze a zdroje. Balíčky závislostí je možné přidat do seznamu, upravit a odstranit.

  Identifikátor musí odpovídat `ID` atributu metadat balíčku závislostí. Zdrojem může být projekt v aktuálním řešení, aktuálně nainstalované rozšíření nebo soubor. Nastavení **How is dependency resolved** (Jak se řeší závislost) může být relativní cesta vnořeného balíčku nebo adresa URL umístění pro stažení závislosti. ID, verze a řešení balíčku závislostí odpovídají `Id` atributům , a `Version` `Location` přidruženého `Dependency` elementu.

## <a name="see-also"></a>Viz také
- [Referenční informace ke schématu rozšíření VSIX 2.0](../extensibility/vsix-extension-schema-2-0-reference.md)
- [Anatomie balíčku VSIX](../extensibility/anatomy-of-a-vsix-package.md)
