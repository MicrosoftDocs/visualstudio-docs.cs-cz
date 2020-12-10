---
title: Začínáme se šablonou projektu VSIX | Microsoft Docs
description: Naučte se, jak pomocí šablony projektu VSIX vytvořit rozšíření nebo zabalit existující rozšíření pro nasazení.
ms.custom: SEO-VS-2020
ms.date: 3/16/2019
ms.topic: how-to
helpviewer_keywords:
- Visual Studio SDK, VSIX project template
ms.assetid: 89fac33e-9380-4723-9b45-048a6e16f0ed
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c6c7c2e12f01b008be6937a8c974f2eea183d594
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2020
ms.locfileid: "96994339"
---
# <a name="get-started-with-the-vsix-project-template"></a>Začínáme se šablonou projektu VSIX

Můžete použít šablonu projektu VSIX k vytvoření rozšíření nebo pro zabalení existující rozšíření pro nasazení. Šablona projektu VSIX má verze Visual Basic i Visual C# a je nainstalována jako součást sady Visual Studio SDK.

 Šablona projektu VSIX se právě skládá ze souboru *source. extension. vsixmanifest* , který obsahuje informace o rozšíření a prostředcích, které dodává.

 Chcete-li najít šablonu projektu VSIX, je nutné nainstalovat sadu Visual Studio SDK. Další informace najdete v tématu [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="deploy-a-custom-project-template-using-the-vsix-project-template"></a>Nasazení vlastní šablony projektu pomocí šablony projektu VSIX

 Následující postup ukazuje, jak použít projekt VSIX k zabalení šablony projektu, kterou můžete sdílet s ostatními vývojáři nebo nahrát do galerie sady Visual Studio.

1. Vytvořte šablonu projektu.

    1. Otevřete projekt, ze kterého chcete vytvořit šablonu. Tento projekt může být libovolného typu projektu.

    2. V nabídce **projekt** klikněte na položku **Exportovat šablonu**. Dokončete kroky průvodce.

         Soubor *. zip* se vytvoří v *%USERPROFILE%\My Documents\Visual studiu {Version} \My exportovaných šablon \\*.

2. Vytvoří prázdný projekt VSIX.

     Vyberte **soubor**  >  **Nový**  >  **projekt**. Do vyhledávacího pole zadejte "VSIX" a vyberte buď **C#** nebo **Visual Basic** verze **projektu VSIX**.

3. Přidejte do projektu soubor *. zip* . Nastavte vlastnost **Kopírovat do výstupního adresáře** na `Copy Always` .

4. V **Průzkumník řešení** dvakrát klikněte na soubor *source. extension. vsixmanifest* a otevřete ho v **Návrháři manifestu VSIX** a proveďte následující změny:

    - Nastavte pole **název produktu** na **Moje šablony projektu**.

    - V poli **ID produktu** nastavte hodnotu **MyProjectTemplate-1**.

    - Nastavte pole **Author** na **Fabrikam**.

    - Nastavte pole **Popis** na **moji šablonu projektu**.

    - V části **assets (prostředky** ) přidejte typ **Microsoft. VisualStudio. ProjectTemplate** a nastavte jeho cestu na název souboru *. zip* .

5. Uložte a zavřete soubor *source. extension. vsixmanifest* .

6. Sestavte projekt.

7. Ve výstupním adresáři dvakrát klikněte na soubor *. vsix* .

8. Zobrazí se okno se zprávou **instalačního programu VSIX** . Postupujte podle pokynů pro instalaci rozšíření.

9. Zavřete Visual Studio a potom ho znovu otevřete.

::: moniker range="vs-2017"

10. Vyberte **rozšíření a aktualizace** (v nabídce **nástroje** ) a vyberte kategorii **šablony** . Jedna z dostupných rozšíření by měla být **Moje šablona projektu**.

::: moniker-end

::: moniker range=">=vs-2019"

10. Vyberte **Spravovat rozšíření** (v nabídce **rozšíření** ) a vyberte kategorii **šablony** . Jedna z dostupných rozšíření by měla být **Moje šablona projektu**.

::: moniker-end

11. Nová šablona projektu se zobrazí v dialogovém okně **Nový projekt** na stejném místě jako původní šablona projektu. Například pokud jste vytvořili šablonu s názvem **Konzola VB** z Visual Basic konzolové aplikace, **Konzola VB** se zobrazí ve stejném podokně jako šablona **konzolové aplikace** Visual Basic.

### <a name="to-specify-the-location-of-the-template-in-the-new-project-dialog-box"></a>Určení umístění šablony v dialogovém okně Nový projekt

1. Složky šablon se nacházejí v adresářích *{cesta instalace sady Visual Studio} \Common7\IDE\ProjectTemplates* a *{Visual Studio Installation Path} \Common7\IDE\ItemTemplates* . Názvy sekcí nejvyšší úrovně v dialogovém okně **Nový projekt** se přesně neshodují s názvy složek šablon. Pokud se liší, použijte název složky šablony.

    Změňte příponu souboru *. vsix* na *. zip* a pak soubor otevřete.

2. Vytvořte novou složku se stejným názvem jako oddíl v dialogovém okně **Nový projekt** , ve kterém by se šablona měla zobrazit.

3. Pokud se šablona zobrazí v podčásti, vytvořte podsložku se stejným názvem.

4. Přesuňte soubor template *. zip* do nové složky.

5. Změňte příponu *. zip* na *. vsix*.

6. Otevřete manifest VSIX.

7. V manifestu VSIX aktualizujte cestu **assetu** šablony tak, aby odkazovala na kořen stromu adresáře, který obsahuje soubor šablony. Například pokud je šablona v *\CSharp\Windows*, odkaz by měl ukazovat na *\CSharp*.
