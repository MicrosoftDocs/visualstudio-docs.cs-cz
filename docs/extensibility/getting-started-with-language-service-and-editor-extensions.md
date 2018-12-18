---
title: Začínáme se službou Language Service a rozšíření editoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: 6b151891-c06d-40b1-9867-42298caa8492
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8b5fa8d0dbe011ef6b960c03d7d95aa776de6933
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49901317"
---
# <a name="get-started-with-language-service-and-editor-extensions"></a>Začínáme s rozšířeními service a editoru jazyka
Rozšíření editoru slouží k přidání služby jazykové vlastnosti zahrnující například sbalování, párování složených závorek, technologie IntelliSense a návrhy, programovacího jazyka nebo jakýkoli typ obsahu. Můžete také přizpůsobit vzhled a chování editoru sady Visual Studio, například text barevné zvýrazňování, okrajů, vylepšení a další vizuální prvky. Můžete také definovat vlastní typ obsahu a definujte vzhled a chování textové zobrazení, ve kterých se zobrazí váš obsah.  
  
 Chcete-li začít psát rozšíření editoru, použijte editor šablony projektů, které se instalují jako součást sady Visual Studio SDK. Visual Studio SDK je ke stažení sady nástrojů, které usnadňují vývoj rozšíření sady Visual Studio pomocí rozšíření VSPackages nebo pomocí Managed Extensibility Framework (MEF).  
  
> [!NOTE]
>  Další informace o sadě Visual Studio SDK naleznete v tématu [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
 Doporučujeme, abyste před Tvorba vlastních rozšíření editoru informace o následujících konceptům a technologiím.  
  
## <a name="the-windows-presentation-foundation-wpf-and-editor-extensions"></a>Rozšíření Windows Presentation Foundation (WPF) a editor  
 Visual Studio editor uživatelské rozhraní (UI) je implementovaný s využitím Windows Presentation Foundation (WPF). WPF poskytuje bohaté možnosti vzhled a konzistentní programovací model, který odděluje visual aspektů kód z obchodní logiky. Při vytváření rozšíření editoru, můžete použít mnoho prvků WPF a funkce. Další informace najdete v tématu [Windows Presentation Foundation](/dotnet/framework/wpf/index).  
  
## <a name="the-managed-extensibility-framework-mef-and-editor-extensions"></a>Rozšíření Managed Extensibility Framework (MEF) a editor  
 Editor sady Visual Studio Managed Extensibility Framework (MEF) používá ke správě jeho součástmi a rozšíření. Rozhraní MEF také umožňuje další vývojářům snadno vytvářet rozšíření pro hostitelskou aplikaci, jako je Visual Studio. V tomto rámci definování rozšíření podle smlouvy MEF a exportujte ho jako součást MEF. Hostitelská aplikace spravuje dílů tím, že je, je registrace a ujistěte se, že se použijí pro správný kontext.  
  
> [!NOTE]
>  Další informace o rozhraní MEF v editoru, najdete v části [Managed Extensibility Framework v editor](../extensibility/managed-extensibility-framework-in-the-editor.md).  
  
## <a name="visual-studio-editor-extension-points-and-extensions"></a>Visual Studio editor Rozšiřovací body a rozšíření  
 Editor Rozšiřovací body jsou součásti MEF, které můžete přizpůsobit a rozšířit. V některých případech můžete rozšířit rozšiřovací bod implementace rozhraní a export spolu s správných metadat. V ostatních případech stačí deklarovat rozšíření a exportujte ho jako konkrétního typu.  
  
 Tady jsou některé základní typy rozšíření editoru:  
  
- Okraje a posuvníky  
  
- Značky  
  
- Vylepšení  
  
- Možnosti  
  
- IntelliSense  
  
  Další informace o bodech rozšíření editoru, najdete v části [Rozšiřovací body služby a editoru jazyka](../extensibility/language-service-and-editor-extension-points.md).  
  
## <a name="deploying-editor-extensions"></a>Nasazení rozšíření editoru  
 V sadě Visual Studio nasadit rozšíření editoru tak, že přidáte soubor metadat s názvem *source.extension.vsixmanifest* k řešení, sestavení řešení a následným přidáním kopii binárních souborů a manifest ve složce, která se označuje do sady Visual Studio. Soubor manifestu definuje základních faktů o rozšíření (například názvu, autora, verze a typu obsahu). Další informace o souboru manifestu VSIX a tom, jak nasadit rozšíření najdete v tématu [rozšíření sady Visual Studio příjemce](../extensibility/shipping-visual-studio-extensions.md).  
  
 Při instalaci rozšíření na počítači zahrnout binární soubory a manifest v podsložce složky, který znáte Visual Studio.  
  
> [!WARNING]
>  Není nutné se starat o podrobnosti manifestů a umístění nasazení, pokud používáte některou ze šablon rozšíření editoru, které jsou zahrnuty v sadě Visual Studio. Šablony obsahují vše potřebné k registraci a nasadit rozšíření.  
  
## <a name="run-extensions-in-the-experimental-instance"></a>Spusťte rozšíření v experimentální instanci  
 Vaše pracovní verze sady Visual Studio můžete izolovat, zatímco vyvíjíte rozšíření nasazením v následující složce experimentální (ve Windows Vista a Windows 7):  
  
 *{%LOCALAPPDATA%}\VisualStudio\10.0Exp\Extensions\\{společnosti}\\{ExtensionID}.*  
  
 kde *% LOCALAPPDATA %* je jméno přihlášeného uživatele, *společnosti* je název společnosti, který vlastní rozšíření, a *ExtensionID* je ID rozšíření.  
  
 Když nasadíte do umístění, experimentální rozšíření, je spuštěna v režimu ladění. Druhou instanci aplikace Visual Studio se spustí a názvem **Microsoft Visual Studio – experimentální instanci**.  
  
## <a name="manage-extensions"></a>Správa rozšíření  
 Rozšíření pro Visual Studio jsou uvedeny v **rozšíření a aktualizace** (na **nástroje** nabídky). Pokud testujete rozšíření v experimentální instanci, je uvedena v **rozšíření a aktualizace** v experimentální instanci, ale není uvedený v instanci vývoje.  
  
 Další informace najdete v tématu [vyhledání a používání rozšíření sady Visual Studio](../ide/finding-and-using-visual-studio-extensions.md).  
  
## <a name="use-templates-to-create-editor-extensions"></a>Použijte šablony k vytvoření rozšíření editoru  
 Editor šablon můžete použít k vytvoření rozšíření MEF, které přizpůsobení třídění, vylepšení a okraje. Existují šablony pro projekty jazyka C# i Visual Basic. Další informace najdete v tématu [vytváření rozšíření pomocí šablony položky editoru](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
 Šablona projektu VSIX můžete použít také k vytvoření rozšíření. Tato šablona obsahuje pouze elementy, které je potřeba nasadit jakýkoli typ rozšíření a zahrnout *source.extension.vsixmanifest* souboru, odkazy na požadovaná sestavení a soubor projektu, který zahrnuje funkci úloh sestavení které umožňují nasadit rozšíření. Další informace najdete v tématu [šablonou projektu VSIX](../extensibility/vsix-project-template.md).  
  
 Můžete také vytvořit editor komponent MEF z rozšíření sady Visual Studio balíček. Najdete v následujících návodech podrobnosti:  
  
-   [Návod: Použití příkazů prostředí s rozšířením editoru](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)  
  
-   [Návod: Použití klávesové zkratky s rozšířením editoru](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)  
  
## <a name="see-also"></a>Viz také:  
 [Jazykové služby a editor Rozšiřovací body](../extensibility/language-service-and-editor-extension-points.md)