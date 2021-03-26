---
title: Začínáme s rozšířeními služby jazyka a editoru
description: Naučte se, jak přidat funkce jazykové služby do libovolného typu obsahu a přizpůsobit vzhled a chování editoru sady Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: 6b151891-c06d-40b1-9867-42298caa8492
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1afec04882d5d52bffac509dd1d1202ccf9ea449
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105057608"
---
# <a name="get-started-with-language-service-and-editor-extensions"></a>Začínáme s rozšířeními služby jazyka a editoru

Rozšíření editoru můžete použít k přidání funkcí jazykové služby, jako je například sbalení, spárování složených závorek, IntelliSense a žárovky, do vlastního programovacího jazyka nebo jakéhokoli typu obsahu. Můžete také přizpůsobit vzhled a chování editoru sady Visual Studio, například barevné zvýraznění, okraje, doplňky a další vizuální prvky. Můžete také definovat vlastní typ obsahu a určit vzhled a chování textových zobrazení, ve kterých se zobrazuje obsah.

 Chcete-li začít s psaním rozšíření editoru, použijte šablony projektů editoru, které jsou nainstalovány jako součást sady Visual Studio SDK. Sada Visual Studio SDK je ke stažení sady nástrojů, které usnadňují vývoj rozšíření sady Visual Studio, a to buď pomocí VSPackage, nebo pomocí Managed Extensibility Framework (MEF).

> [!NOTE]
> Další informace o sadě Visual Studio SDK naleznete v tématu [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

 Doporučujeme, abyste se dozvěděli o následujících konceptech a technologiích před zápisem vlastních rozšíření editoru.

## <a name="the-windows-presentation-foundation-wpf-and-editor-extensions"></a>Rozšíření Windows Presentation Foundation (WPF) a editoru

 Uživatelské rozhraní (UI) editoru sady Visual Studio je implementováno pomocí Windows Presentation Foundation (WPF). WPF poskytuje bohatou vizuální prostředí a jednotný programovací model, který odděluje vizuální aspekty kódu z obchodní logiky. Když vytváříte rozšíření editoru, můžete použít spoustu prvků a funkcí WPF. Další informace najdete v tématu [Windows Presentation Foundation](/dotnet/framework/wpf/index).

## <a name="the-managed-extensibility-framework-mef-and-editor-extensions"></a>Rozšíření Managed Extensibility Framework (MEF) a editoru

 Editor sady Visual Studio používá ke správě svých komponent a rozšíření Managed Extensibility Framework (MEF). Rozhraní MEF také umožňuje vývojářům snadněji vytvářet rozšíření pro hostitelskou aplikaci, jako je Visual Studio. V tomto rozhraní definujete rozšíření podle kontraktu MEF a vyexportujete jako součást MEF. Hostitelská aplikace spravuje části součásti jejich vyhledáním, jejich registrací a zajištěním, že jsou aplikovány na správný kontext.

> [!NOTE]
> Další informace o MEF v editoru naleznete v tématu [Managed Extensibility Framework v editoru](../extensibility/managed-extensibility-framework-in-the-editor.md).

## <a name="visual-studio-editor-extension-points-and-extensions"></a>Rozšiřující body a rozšíření editoru sady Visual Studio

 Body rozšíření editoru jsou části komponenty MEF, které lze přizpůsobit a rozšířit. V některých případech rozšířit rozšiřující bod implementací rozhraní a jeho export společně se správnými metadaty. V ostatních případech jste právě deklarovali rozšíření a exportovali ho jako konkrétní typ.

 Následuje několik základních druhů rozšíření editoru:

- Okraje a posuvníky

- Značky

- Grafických doplňků

- Možnosti

- IntelliSense

  Další informace o bodech rozšíření editoru naleznete v tématu [jazykové služby a rozšiřovací body editoru](../extensibility/language-service-and-editor-extension-points.md).

## <a name="deploying-editor-extensions"></a>Nasazení rozšíření editoru

 V aplikaci Visual Studio nasadíte rozšíření editoru přidáním souboru metadat s názvem *source. extension. vsixmanifest* do řešení, sestavením řešení a následným přidáním kopie binárních souborů a manifestu do složky, která je známá v aplikaci Visual Studio. Soubor manifestu definuje základní fakta o rozšíření (například název, autor, verze a typ obsahu). Další informace o souboru manifestu VSIX a o tom, jak nasadit rozšíření, najdete v tématu [dodávání rozšíření sady Visual Studio](../extensibility/shipping-visual-studio-extensions.md).

 Když nainstalujete rozšíření na počítač, zahrňte binární soubory a manifest do podsložky složky, která je známá pro Visual Studio.

> [!WARNING]
> Pokud použijete některou ze šablon rozšiřitelnosti editoru, které jsou součástí sady Visual Studio, nemusíte si dělat starosti s podrobnostmi manifestů a umístění nasazení. Šablony obsahují všechno, co je potřeba k registraci a nasazení rozšíření.

## <a name="run-extensions-in-the-experimental-instance"></a>Spustit rozšíření v experimentální instanci

 Svou pracovní verzi sady Visual Studio můžete zaizolovaně vymezit, když vyvíjíte rozšíření nasazením v následující experimentální složce (v systému Windows Vista a Windows 7):

 *{% LOCALAPPDATA%} \VisualStudio\10.0Exp\Extensions \\ {Company} \\ {ExtensionID}*

 kde *% localappdata%* je jméno přihlášeného uživatele, *Společnost* je název společnosti, která rozšíření vlastní, a *ExtensionID* je ID rozšíření.

 Když nasadíte rozšíření do experimentálního umístění, spustí se v režimu ladění. Spustí se druhá instance sady Visual Studio a je pojmenována **Microsoft Visual Studio-experimentální instance**.

## <a name="manage-extensions"></a>Správa rozšíření

 Rozšíření pro Visual Studio jsou uvedená v části **rozšíření a aktualizace** (v nabídce **nástroje** ). Pokud testujete rozšíření v experimentální instanci, je uveden v části **rozšíření a aktualizace** v experimentální instanci, ale není uvedena v instanci vývoje.

 Další informace najdete v tématu [hledání a používání rozšíření sady Visual Studio](../ide/finding-and-using-visual-studio-extensions.md).

## <a name="use-templates-to-create-editor-extensions"></a>Použití šablon k vytvoření rozšíření editoru

 Šablony editoru lze použít k vytvoření rozšíření MEF, která přizpůsobují třídění, doplňky a okraje. Existují šablony pro projekty C# i Visual Basic. Další informace naleznete v tématu [Vytvoření rozšíření pomocí šablony položky editoru](../extensibility/creating-an-extension-with-an-editor-item-template.md).

 K vytvoření rozšíření můžete použít také šablonu projektu VSIX. Tato šablona poskytuje pouze prvky, které jsou požadovány k nasazení jakéhokoli typu rozšíření, včetně souboru *source. extension. vsixmanifest* , požadovaných odkazů na sestavení a souboru projektu, který obsahuje úlohy sestavení, které umožňují nasazení rozšíření. Další informace naleznete v tématu [Šablona projektu VSIX](../extensibility/vsix-project-template.md).

 Můžete také vytvořit Editor komponent MEF z rozšíření balíčku sady Visual Studio. Podrobnosti najdete v následujících návodech:

- [Návod: použití příkazu shell s rozšířením editoru](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)

- [Návod: použití klávesových zkratek s rozšířením editoru](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)

## <a name="see-also"></a>Viz také

- [Rozšiřovací body služby jazyka a editoru](../extensibility/language-service-and-editor-extension-points.md)
