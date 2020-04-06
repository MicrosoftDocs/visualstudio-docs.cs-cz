---
title: Začínáme se šablonou projektu VSIX | Dokumenty společnosti Microsoft
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio SDK, VSIX project template
ms.assetid: 89fac33e-9380-4723-9b45-048a6e16f0ed
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 773e9e6891599cd9672888d0521e94891e0d9f41
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711249"
---
# <a name="get-started-with-the-vsix-project-template"></a>Začínáme se šablonou Projektu VSIX

Šablonu Projektu VSIX můžete použít k vytvoření rozšíření nebo k zabalení existujícího rozšíření pro nasazení. Šablona projektu VSIX obsahuje verze jazyka Visual Basic i Visual C# a je nainstalována jako součást sady Visual Studio SDK.

 Šablona projektu VSIX se skládá pouze ze souboru *source.extension.vsixmanifest,* který obsahuje informace o rozšíření a datových zdrojích, které dodává.

 Chcete-li najít šablonu projektu VSIX, je nutné nainstalovat sady Visual Studio SDK. Další informace naleznete v [tématu Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="deploy-a-custom-project-template-using-the-vsix-project-template"></a>Nasazení vlastní šablony projektu pomocí šablony projektu VSIX

 Následující kroky ukazují, jak pomocí projektu VSIX zabalit šablonu projektu, kterou můžete sdílet s jinými vývojáři nebo nahrát do galerie Visual Studio.

1. Vytvořte šablonu projektu.

    1. Otevřete projekt, ze kterého chcete vytvořit šablonu. Tento projekt může být libovolného typu projektu.

    2. V nabídce **Project** klepněte na **položku Exportovat šablonu**. Proveďte kroky průvodce.

         Soubor *ZIP* je vytvořen v *%USERPROFILE%\Dokumenty\Visual Studio {version}\Moje\\exportované šablony*.

2. Vytvořte prázdný projekt VSIX.

     Vyberte **Soubor** > **nový** > **projekt**. Do vyhledávacího pole zadejte "vsix" a vyberte verzi aplikace **C#** nebo **Visual Basic** **aplikace VSIX Project**.

3. Přidejte soubor *ZIP* do projektu. Nastavte vlastnost Kopírovat do `Copy Always` **výstupního adresáře** na .

4. V **Průzkumníku řešení**poklepejte na soubor *source.extension.vsixmanifest,* abyste jej otevřeli v **Návrháři manifestů VSIX**, a proveďte následující změny:

    - Nastavte pole **Název produktu** na **šablonu projektu**.

    - Nastavte pole **ID produktu** na **MyProjectTemplate - 1**.

    - Nastavte pole **Autor** na **Fabrikam**.

    - Nastavte pole **Popis** na **šablonu projektu**.

    - V části **Datové zdroje** přidejte typ **Microsoft.VisualStudio.ProjectTemplate** a nastavte jeho cestu k názvu souboru *ZIP.*

5. Uložte a zavřete soubor *source.extension.vsixmanifest.*

6. Sestavte projekt.

7. Ve výstupním adresáři poklepejte na soubor *.vsix.*

8. Zobrazí se okno se zprávou **Instalační služby VSIX.** Podle pokynů nainstalujte rozšíření.

9. Zavřete Visual Studio a znovu ji otevřete.

::: moniker range="vs-2017"

10. Vyberte **Rozšíření a aktualizace** (v nabídce **Nástroje)** a vyberte kategorii **Šablony.** Jedním z dostupných rozšíření by měla být **šablona projektu**.

::: moniker-end

::: moniker range=">=vs-2019"

10. Vyberte **Spravovat rozšíření** (v nabídce **Rozšíření)** a vyberte kategorii **Šablony.** Jedním z dostupných rozšíření by měla být **šablona projektu**.

::: moniker-end

11. Nová šablona projektu se zobrazí v dialogovém okně **Nový projekt** na stejném místě jako původní šablona projektu. Pokud jste například vytvořili šablonu s názvem **Konzola VB** z aplikace konzoly Visual Basic, **konzola VB** se zobrazí ve stejném podokně jako šablona **aplikace konzoly Visual** Basic.

### <a name="to-specify-the-location-of-the-template-in-the-new-project-dialog-box"></a>Určení umístění šablony v dialogovém okně Nový projekt

1. Složky šablon jsou umístěny v adresářích *{Visual Studio Installation Path}\Common7\IDE\ProjectTemplates* a *{Visual Studio Installation Path}\Common7\IDE\ItemTemplates.* Názvy oddílů nejvyšší úrovně v dialogovém okně **Nový projekt** se přesně neshodují s názvy složek šablon. Pokud se liší, použijte název složky šablony.

    Změňte příponu *souboru .vsix* na *zip*a otevřete soubor.

2. Vytvořte novou složku se stejným názvem jako část dialogového okna **Nový projekt,** ve které by se měla šablona zobrazit.

3. Pokud se má šablona zobrazit v podsekci, vytvořte podsložku se stejným názvem.

4. Přesuňte soubor *ZIP* šablony do nové složky.

5. Změňte příponu *ZIP* na *.vsix*.

6. Otevřete manifest VSIX.

7. V manifestu VSIX aktualizujte cestu **k datovému zdroji** šablony tak, aby směřovat ke kořenovému adresáři adresářového stromu, který obsahuje soubor šablony. Pokud je například šablona v *\CSharp\Windows*, měl by odkaz odkazovat na *\CSharp*.
