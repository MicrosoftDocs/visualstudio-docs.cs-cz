---
title: Šablona projektu VSIX | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- deploy packages
- publish extension
ms.assetid: b6c82167-e2a5-4cff-8c8b-2d72e2a9092c
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c2b06582e1de7939e34f8fa49aa1cc9435010789
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51733863"
---
# <a name="vsix-project-template"></a>Šablona projektu VSIX
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Použijte šablonu projektu VSIX zabalit jeden nebo více rozšíření sady Visual Studio v projektu VSIX a potom publikujete balíček na [Galerie sady Visual Studio](http://go.microsoft.com/fwlink/?LinkID=123847) webu.  
  
 VSIX instalace podporuje rozšíření VSPackages, sestavení, MEF komponenty, šablony projektů, šablony položek, ovládací prvky panelu nástrojů a rozšíření vlastních typů.  
  
> [!NOTE]
>  Pokud chcete používat projekty VSIX, musíte nainstalovat Visual Studio SDK. Další informace o sadě Visual Studio SDK naleznete v tématu [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="where-to-find-the-vsix-project-template"></a>Kde najít šablonou projektu VSIX  
 Šablona projektu VSIX je k dispozici v **nový projekt** dialogové okno. Rozbalte buď **jazyka Visual Basic** uzlu nebo **Visual C#** uzel a klikněte na tlačítko **rozšiřitelnost**.  
  
> [!TIP]
>  Ujistěte se, že rozhraní .NET Framework 4.5 nebo vyšší je zadán v rozevírací nabídce v horní části **nový projekt** dialogové okno.  
  
## <a name="uses-of-the-vsix-project-template"></a>Použití šablony projektu VSIX  
 Šablona projektu VSIX má dvě hlavní využití:  
  
- K nasazení šablony projektů, šablony položek a další rozšíření, které ještě nemají podporu VSIX.  
  
- Zabalit výstupy několik rozšíření do balíčku jedno nasazení.  
  
  Není nutné použít šablonu projektu VSIX k nasazení rozšíření VSPackages nebo jiných typů rozšíření, které už mají podporu VSIX.  
  
## <a name="packaging-an-extension-in-an-empty-vsix-project"></a>Vytvoření balíčku rozšíření v projektu VSIX prázdný  
 Můžete zabalit existující rozšíření nebo rozšíření, která ještě nemá podporu obalením v prázdný projekt VSIX VSIX. Rozšíření bude zabalena musí být typu, který je podporován [VSIX schématu](../extensibility/vsix-extension-schema-2-0-reference.md).  
  
#### <a name="to-package-an-extension-by-using-a-vsix-project"></a>Balíček rozšíření pomocí projektu VSIX  
  
1.  Sestavení projektů, které tvoří rozšíření.  
  
2.  Vytvořte projekt VSIX s použitím **projekt VSIX** šablony.  
  
     Source.extension.vsixmanifest se otevře v **Manifest Designer**.  
  
3.  Na **prostředky** , vyberte **nový** tlačítko.  
  
     **Přidat nové aktivum** zobrazí se dialogové okno.  
  
4.  V **typ** , zvolte typ rozšíření přidat.  
  
5.  Chcete-li přidat rozšíření nebo obsah elementu, který je součástí aktuálního řešení (například šablonu položky nebo zkompilovaného sestavení), postupujte následovně:  
  
    1.  V **zdroj** klikněte na položku **projekt v aktuálním řešení**.  
  
    2.  V **projektu** , zvolte název rozšíření.  
  
    3.  V **vložit do této složky** zadejte název složky, do které se má prostředek pro vložení a klikněte na tlačítko **OK** tlačítko.  
  
6.  Přidání rozšíření nebo element content, který není součástí aktuálního řešení, proveďte následující kroky:  
  
    1.  V **zdroj** seznamu, zvolte **soubor v systému souborů**.  
  
    2.  V **cesta** pole, zadejte úplnou cestu k souboru rozšíření zkompilovaných nebo komprimované nebo použít **Procházet** tlačítko, přejděte k souboru.  
  
    3.  V **vložit do této složky** zadejte název složky, do které se má prostředek pro vložení a klikněte na tlačítko **OK** tlačítko.  
  
7.  Pokud chcete, aby váš balíček zahrnout další rozšíření, je přidáte stejným způsobem.  
  
8.  Sestavte řešení.  
  
     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] : sestavení souboru .vsix, který obsahuje soubor manifestu VSIX, souboru [Content_Types] .xml a všechny prostředky rozšíření, které jste přidali do projektu.  
  
## <a name="see-also"></a>Viz také  
 [VSIX Extension Schema 2.0 – referenční informace](../extensibility/vsix-extension-schema-2-0-reference.md)   
 [Hledání a používání rozšíření sady Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)

