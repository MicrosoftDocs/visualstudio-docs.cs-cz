---
title: Šablona projektu VSIX | Microsoft Docs
description: Naučte se používat šablonu projektu VSIX k zabalení rozšíření sady Visual Studio v projektu VSIX a pak balíček publikovat na Visual Studio Marketplace.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- deploy packages
- publish extension
ms.assetid: b6c82167-e2a5-4cff-8c8b-2d72e2a9092c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 76e4301843cc318b60940948fee4b618860e7bae
ms.sourcegitcommit: dd96a95d87a039525aac86abe689c30e2073ae87
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/04/2021
ms.locfileid: "97863875"
---
# <a name="vsix-project-template"></a>Šablona projektu VSIX

Můžete použít šablonu projektu VSIX k zabalení jednoho nebo více rozšíření sady Visual Studio v projektu VSIX a pak balíček publikovat na webu [Visual Studio Marketplace](https://marketplace.visualstudio.com/) .

 Nasazení VSIX podporuje VSPackage, sestavení, komponenty MEF, šablony projektů, šablony položek, ovládací prvky panelu nástrojů a vlastní typy rozšíření.

> [!NOTE]
> Chcete-li použít VSIX projekty, je nutné nainstalovat sadu Visual Studio SDK. Další informace o sadě Visual Studio SDK naleznete v tématu [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="where-to-find-the-vsix-project-template"></a>Kde najít šablonu projektu VSIX

Šablona projektu VSIX je k dispozici v dialogovém okně **Nový projekt** hledáním "VSIX".  Existuje verze C# i Visual Basic.

> [!TIP]
> Ujistěte se, že je v rozevíracím seznamu v horní části dialogového okna **Nový projekt** uvedena .NET Framework 4,5 nebo vyšší.

## <a name="uses-of-the-vsix-project-template"></a>Použití šablony projektu VSIX

Šablona projektu VSIX má dvě hlavní použití:

- Nasazení šablon projektů, šablon položek a rozšíření.

- Chcete-li zabalit výstupy více rozšíření do jednoho balíčku pro nasazení.

## <a name="packaging-an-extension-in-an-empty-vsix-project"></a>Balení rozšíření do prázdného projektu VSIX

Můžete zabalit existující rozšíření nebo rozšíření, které ještě nepodporuje VSIX, zabalením do prázdného projektu VSIX. Rozšíření, které má být zabaleno, musí být typu, který je podporován [schématem VSIX](../extensibility/vsix-extension-schema-2-0-reference.md).

### <a name="to-package-an-extension-by-using-a-vsix-project"></a>Zabalení rozšíření pomocí projektu VSIX

1. Sestavte projekty, které tvoří vaše rozšíření.

2. Vytvořte projekt VSIX pomocí šablony **projektu VSIX** .

    *Zdrojový. extension. vsixmanifest* se otevře v **Návrháři manifestu**.

3. Na kartě **assets (prostředky** ) klikněte na tlačítko **Nový** .

    Zobrazí se dialogové okno **Přidat nový prostředek** .

4. V seznamu **typ** vyberte typ rozšíření, které chcete přidat.

5. Chcete-li přidat rozšíření nebo prvek obsahu, který je součástí aktuálního řešení (například šablona položky nebo zkompilované sestavení), proveďte následující kroky:

   1. V seznamu **zdroj** vyberte **projekt v aktuálním řešení**.

   2. V seznamu **projekt** vyberte název rozšíření.

   3. V poli **Vložit do této složky** zadejte název složky, do které chcete vložit Asset, a pak klikněte na tlačítko **OK** .

6. Chcete-li přidat rozšíření nebo prvek obsahu, který není součástí aktuálního řešení, proveďte následující kroky:

   1. V rozevíracím seznamu **zdroj** vyberte možnost **soubor v systému souborů**.

   2. Do pole **cesta** zadejte úplnou cestu k kompilovanému nebo komprimovanému souboru rozšíření nebo použijte tlačítko **Procházet** a přejděte k souboru.

   3. V poli **Vložit do této složky** zadejte název složky, do které chcete vložit Asset, a pak klikněte na tlačítko **OK** .

7. Pokud chcete, aby balíček zahrnoval další rozšíření, přidejte je stejným způsobem.

8. Sestavte řešení.

    [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Vytvoří soubor *. vsix* , který obsahuje soubor manifestu VSIX, soubor [Content_Types]*. XML* a všechny rozšiřující prostředky, které jste přidali do projektu.

## <a name="see-also"></a>Viz také

- [Referenční dokumentace schématu rozšíření VSIX 2,0](../extensibility/vsix-extension-schema-2-0-reference.md)
- [Vyhledání a používání rozšíření sady Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)
