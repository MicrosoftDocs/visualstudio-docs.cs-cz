---
title: Šablona projektu VSIX | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- deploy packages
- publish extension
ms.assetid: b6c82167-e2a5-4cff-8c8b-2d72e2a9092c
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2386f1be805f6347fc32fba4ee8bfe57c8602329
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64825462"
---
# <a name="vsix-project-template"></a>Šablona projektu VSIX
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete použít šablonu projektu VSIX k zabalení jednoho nebo více rozšíření sady Visual Studio v projektu VSIX a pak balíček publikovat na webu [Visual Studio Marketplace](https://marketplace.visualstudio.com/) .  
  
 Nasazení VSIX podporuje VSPackage, sestavení, komponenty MEF, šablony projektů, šablony položek, ovládací prvky panelu nástrojů a vlastní typy rozšíření.  
  
> [!NOTE]
> Chcete-li použít VSIX projekty, je nutné nainstalovat sadu Visual Studio SDK. Další informace o sadě Visual Studio SDK naleznete v tématu [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="where-to-find-the-vsix-project-template"></a>Kde najít šablonu projektu VSIX  
 Šablona projektu VSIX je k dispozici v dialogovém okně **Nový projekt** . Rozbalte uzel **Visual Basic** nebo uzel **Visual C#** a pak zvolte možnost **rozšiřitelnost**.  
  
> [!TIP]
> Ujistěte se, že je v rozevíracím seznamu v horní části dialogového okna **Nový projekt** uvedena .NET Framework 4,5 nebo vyšší.  
  
## <a name="uses-of-the-vsix-project-template"></a>Použití šablony projektu VSIX  
 Šablona projektu VSIX má dvě hlavní použití:  
  
- Pro nasazení šablon projektů, šablon položek a dalších rozšíření, která ještě nemají podporu VSIX.  
  
- Chcete-li zabalit výstupy více rozšíření do jednoho balíčku pro nasazení.  
  
  Nemusíte používat šablonu projektu VSIX k nasazování VSPackage nebo jiných druhů rozšíření, která již mají podporu VSIX.  
  
## <a name="packaging-an-extension-in-an-empty-vsix-project"></a>Balení rozšíření do prázdného projektu VSIX  
 Můžete zabalit existující rozšíření nebo rozšíření, které ještě nepodporuje VSIX, zabalením do prázdného projektu VSIX. Rozšíření, které má být zabaleno, musí být typu, který je podporován [schématem VSIX](../extensibility/vsix-extension-schema-2-0-reference.md).  
  
#### <a name="to-package-an-extension-by-using-a-vsix-project"></a>Zabalení rozšíření pomocí projektu VSIX  
  
1. Sestavte projekty, které tvoří vaše rozšíření.  
  
2. Vytvořte projekt VSIX pomocí šablony **projektu VSIX** .  
  
     Zdrojový. extension. vsixmanifest se otevře v **Návrháři manifestu**.  
  
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
  
     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Vytvoří soubor. vsix, který obsahuje soubor manifestu VSIX, soubor [Content_Types]. XML a všechny rozšiřující prostředky, které jste přidali do projektu.  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace schématu rozšíření VSIX 2,0](../extensibility/vsix-extension-schema-2-0-reference.md)   
 [Hledání a používání rozšíření Visual Studia](../ide/finding-and-using-visual-studio-extensions.md)
