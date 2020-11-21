---
title: Hledání odkazů v kódu
description: Přečtěte si o příkazu Najít všechny odkazy, kde najdete odkazy na konkrétní prvky kódu ve vašem kódu.
ms.custom: SEO-VS-2020
ms.date: 09/26/2017
ms.topic: conceptual
helpviewer_keywords:
- code editor, find all references
- find all references
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d5ee6a0792c5dbfa1661018e75806499d1aa1028
ms.sourcegitcommit: 66cda27b63c9b55782b1db223a6dbda9f8cabe13
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2020
ms.locfileid: "95006546"
---
# <a name="find-references-in-your-code"></a>Hledání odkazů v kódu

Pomocí příkazu **Najít všechny odkazy** můžete najít, kde se v rámci základu kódu odkazuje na konkrétní prvky kódu. Příkaz **Najít všechny odkazy** je k dispozici v nabídce kontextu (klikněte pravým tlačítkem myši) prvku, na který chcete najít odkazy. Pokud jste uživatel klávesnice, stiskněte klávesy **SHIFT + F12**.

Výsledky se zobrazí v okně nástroje s názvem **\<element> odkazy**, kde *element* je název položky, kterou hledáte. Panel nástrojů v okně **odkazy** vám umožní:
- Změna rozsahu hledání v rozevíracím seznamu. Můžete se rozhodnout, že budete hledat jenom v změněných dokumentech až do celého řešení.
- Kliknutím na tlačítko **Kopírovat** zkopírujte vybranou odkazovanou položku.
- Zvolte tlačítka pro přechod na další nebo předchozí umístění v seznamu nebo stiskněte klávesy **F8** a **Shift + F8** .
- Kliknutím na tlačítko **Vymazat všechny filtry** odeberte všechny filtry vrácených výsledků.
- Změňte způsob seskupení vrácených položek výběrem nastavení v rozevíracím seznamu **Seskupit podle:** .
- Aktuální okno výsledků hledání nechte kliknutím na tlačítko **zachovat výsledky** . Když vyberete toto tlačítko, aktuální výsledky hledání zůstanou v tomto okně a nové výsledky hledání se zobrazí v novém okně nástroje.
- Vyhledá řetězce v rámci výsledků hledání zadáním textu do textového pole **Hledat všechny odkazy** .

Můžete také umístit ukazatel myši na libovolný výsledek hledání a zobrazit náhled odkazu.

![Podokno nástrojů najít všechny odkazy](../ide/media/vside_findallreferences.png)

## <a name="navigate-to-references"></a>Přejít na odkazy
K přechodu na odkazy v okně **odkazy** můžete použít následující metody:

- Stisknutím klávesy **F8** přejděte na další odkaz nebo stiskněte **Shift + F8** a přejděte na předchozí odkaz.
- Stiskněte klávesu **ENTER** na odkaz, nebo na ni poklikejte, abyste na ni mohli přejít v kódu.
- V nabídce kliknutím pravým tlačítkem (kontextová nabídka) pro odkaz vyberte příkaz **Přejít na předchozí umístění** nebo **Přejít na další umístění** .
- Vyberte **šipky nahoru** a **dolů** (pokud jsou povolené v dialogovém okně **Možnosti** ). Pokud chcete tuto funkci povolit, na panelu nabídek zvolte možnosti **nástroje**  >  **Options**  >  **Environment**  >  **karty prostředí a Windows**  >  **Preview** a potom vyberte možnost **povolit otevírání nových souborů na kartě náhled** a **Zobrazit náhled vybraných souborů v polích výsledky hledání** .

## <a name="change-reference-groupings"></a>Změnit seskupení odkazů
Ve výchozím nastavení se odkazy seskupují podle projektu a pak podle definice. Toto pořadí seskupení ale můžete změnit změnou nastavení v rozevíracím seznamu **Seskupit podle:** na panelu nástrojů. Můžete ho například změnit z výchozího nastavení **projektu, pak definice** na **definice, projekt** i další nastavení.

Pro **definici** a **projekt** se používají dvě výchozí skupiny, ale můžete přidat další kliknutím na příkaz **seskupení** v místní nabídce a kliknutí pravým tlačítkem vybrané položky. Přidání více seskupení může být užitečné, pokud vaše řešení obsahuje velké množství souborů a cest.

## <a name="filter-by-reference-type-in-net"></a>Filtrovat podle typu odkazu v .NET
V jazyce C# nebo Visual Basic má okno najít odkazy sloupec typu, ve kterém je uveden typ odkazu, který byl nalezen. Tento sloupec lze použít k filtrování podle typu odkazu kliknutím na ikonu filtru, která se zobrazí při najetí myší na záhlaví sloupce. Odkazy lze filtrovat podle typu čtení, zápis, odkaz, název, obor názvů a typ.

![Sloupec typu okna hledání odkazů ](../ide/media/vside_findallreferencesKind.png)

## <a name="see-also"></a>Viz také

- [Navigace v kódu](../ide/navigating-code.md)
