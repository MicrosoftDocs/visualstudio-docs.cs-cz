---
title: Začínáme s jazykovými službami a rozšířeními editoru | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: 6b151891-c06d-40b1-9867-42298caa8492
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7894efc477e0c406cf8e85f4d3d31df4f2ef97c5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711313"
---
# <a name="get-started-with-language-service-and-editor-extensions"></a>Začínáme s jazykovými službami a rozšířeními editoru
Pomocí rozšíření editoru můžete přidat funkce jazykových služeb, jako je osnova, shoda složených závorek, technologie IntelliSense a žárovky, do vlastního programovacího jazyka nebo do libovolného typu obsahu. Můžete také přizpůsobit vzhled a chování editoru sady Visual Studio, například vybarvení textu, okraje, vylepšení a další vizuální prvky. Můžete také definovat vlastní typ obsahu a určit vzhled a chování zobrazení textu, ve kterých se obsah zobrazuje.

 Chcete-li začít psát rozšíření editoru, použijte šablony projektu editoru, které jsou nainstalovány jako součást sady Visual Studio SDK. Sada Visual Studio SDK je sada nástrojů ke stažení, které usnadňují vývoj rozšíření sady Visual Studio, buď pomocí VSPackages nebo pomocí rozhraní MEF spravované rozšiřitelnosti (MEF).

> [!NOTE]
> Další informace o sadě Visual Studio SDK naleznete v [tématu Visual Studio SDK](../extensibility/visual-studio-sdk.md).

 Doporučujeme, abyste se před napsáním vlastních rozšíření editoru dozvěděli o následujících konceptech a technologiích.

## <a name="the-windows-presentation-foundation-wpf-and-editor-extensions"></a>Rozšíření Windows Presentation Foundation (WPF) a editor
 Uživatelské rozhraní editoru Visual Studio je implementováno pomocí Windows Presentation Foundation (WPF). WPF poskytuje bohaté vizuální prostředí a konzistentní programovací model, který odděluje vizuální aspekty kódu z obchodní logiky. Při vytváření rozšíření editoru můžete použít mnoho prvků a funkcí WPF. Další informace naleznete v [tématu Windows Presentation Foundation](/dotnet/framework/wpf/index).

## <a name="the-managed-extensibility-framework-mef-and-editor-extensions"></a>Rozhraní MEF (Managed Extensibility Framework) a editor
 Editor Visual Studio používá spravované rozhraní pro rozšiřitelnost (MEF) ke správě jeho součásti a rozšíření. MEF také umožňuje vývojářům snadněji vytvářet rozšíření pro hostitelskou aplikaci, jako je Visual Studio. V tomto rámci definujete rozšíření podle smlouvy MEF a exportujete jej jako součást MEF. Hostitelská aplikace spravuje součásti tím, že je najde, zaregistruje a zajistí, aby byly použity ve správném kontextu.

> [!NOTE]
> Další informace o MEF v editoru naleznete v tématu [Spravované rozšiřitelnost rozhraní v editoru](../extensibility/managed-extensibility-framework-in-the-editor.md).

## <a name="visual-studio-editor-extension-points-and-extensions"></a>Rozšiřující body a rozšíření editoru Visual Studio
 Rozšiřující body editoru jsou součásti MEF, které můžete přizpůsobit a rozšířit. V některých případech rozšířit bod rozšíření implementací rozhraní a exportu spolu se správnými metadaty. V ostatních případech stačí deklarovat rozšíření a exportovat jako určitý typ.

 Následují některé základní druhy rozšíření editoru:

- Okraje a posuvníky

- Značky

- Ozdoby

- Možnosti

- IntelliSense

  Další informace o koncových bodech editoru naleznete [v tématu Language service and editor extension points](../extensibility/language-service-and-editor-extension-points.md).

## <a name="deploying-editor-extensions"></a>Nasazení rozšíření editoru
 V sadě Visual Studio nasadíte rozšíření editoru přidáním souboru metadat s názvem *source.extension.vsixmanifest* do řešení, sestavení řešení a potom přidání kopie binárních souborů a manifestu ve složce, která je známá Visual Studio. Soubor manifestu definuje základní fakta o příponu (například název, autor, verze a typ obsahu). Další informace o souboru manifestu VSIX a o nasazení rozšíření naleznete [v tématu Ship Visual Studio extensions](../extensibility/shipping-visual-studio-extensions.md).

 Při instalaci rozšíření v počítači, zahrnout binární soubory a manifest do podsložky, která je známá Visual Studio.

> [!WARNING]
> Pokud použijete některou ze šablon rozšiřitelnosti editoru, které jsou součástí sady Visual Studio, nemusíte se starat o podrobnosti o manifestech a umístěních nasazení. Šablony obsahují vše, co je nutné k registraci a nasazení rozšíření.

## <a name="run-extensions-in-the-experimental-instance"></a>Spuštění rozšíření v experimentální instanci
 Pracovní verzi sady Visual Studio můžete izolovat při vývoji rozšíření nasazením v následující experimentální složce (v systémech Windows Vista a Windows 7):

 *{%LOCALAPPDATA%}\VisualStudio\10.0Exp\Extensions\\{Company}\\{ExtensionID}*

 kde *%LOCALAPPDATA%* je název přihlášeného uživatele, *Společnost* je název společnosti, která rozšíření vlastní, a *ExtensionID* je ID rozšíření.

 Při nasazení rozšíření do experimentálníumístění, spustí v režimu ladění. Druhá instance sady Visual Studio je spuštěna a má název **Microsoft Visual Studio - Experimental Instance**.

## <a name="manage-extensions"></a>Správa rozšíření
 Rozšíření sady Visual Studio jsou uvedena v **části Rozšíření a aktualizace** (v nabídce **Nástroje).** Pokud testujete rozšíření v experimentální instanci, je uveden v **rozšíření a aktualizace** v experimentální instanci, ale není uveden v instanci vývoje.

 Další informace naleznete v [tématu Hledání a použití rozšíření sady Visual Studio](../ide/finding-and-using-visual-studio-extensions.md).

## <a name="use-templates-to-create-editor-extensions"></a>Použití šablon k vytvoření rozšíření editoru
 Šablony editoru můžete použít k vytvoření rozšíření MEF, které přizpůsobují třídění, vylepšení a okraje. Existují šablony pro projekty jazyka C# i Visual Basic. Další informace naleznete [v tématu Vytvoření rozšíření se šablonou položky editoru](../extensibility/creating-an-extension-with-an-editor-item-template.md).

 Můžete také použít šablonu Projektu VSIX k vytvoření rozšíření. Tato šablona obsahuje pouze prvky, které jsou nutné k nasazení jakéhokoli druhu rozšíření a zahrnují soubor *source.extension.vsixmanifest,* požadované odkazy na sestavení a soubor projektu, který obsahuje úlohy sestavení, které umožňují nasadit rozšíření. Další informace naleznete [v tématu Šablona projektu VSIX](../extensibility/vsix-project-template.md).

 Můžete také vytvořit editor MEF komponenty z rozšíření balíček Visual Studio. Podrobnosti naleznete v následujících návodech:

- [Návod: Použití příkazu prostředí s rozšířením editoru](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)

- [Návod: Použití klávesové zkratky s rozšířením editoru](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)

## <a name="see-also"></a>Viz také
- [Jazykové služby a rozšiřující body editoru](../extensibility/language-service-and-editor-extension-points.md)
