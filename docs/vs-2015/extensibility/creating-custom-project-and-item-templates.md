---
title: Vytváření vlastních šablon projektů a položek
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 586da5dc-f678-402b-afd0-0332959fd7a6
caps.latest.revision: 11
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c6875e13baa83d349020f50a3fe448a87ec5fd30
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197395"
---
# <a name="creating-custom-project-and-item-templates"></a>Vytváření vlastních šablon projektů a položek
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sada Visual Studio SDK obsahuje šablony projektu, které vytvoří vlastní šablonu projektu a šablonu vlastní položky. Tyto šablony obsahují některé běžné náhrady parametrů a sestavování jako soubory zip. Nejsou nasazeny automaticky a nejsou k dispozici v experimentální instanci. Zkopírujte soubor zip do umístění, které jste

Šablony pro vytváření šablon umožňují zahrnout šablony do větších rozšíření. Zahrnutí šablon v rozšířeních umožňuje implementovat řízení verze ve zdrojových souborech a vytvořit skupinu projektů šablon do jednoho balíčku VSIX.

V případě scénářů pro základní vytváření šablon byste měli použít průvodce **exportem šablony** , který vrací výstup do komprimovaného souboru. Další informace o vytváření základních šablon naleznete v tématu [vytváření šablon projektů a položek](../ide/creating-project-and-item-templates.md).

Od sady Visual Studio 2017 se již neprovádí vyhledávání vlastních šablon projektů a položek. Místo toho musí rozšíření poskytnout soubory manifestu šablony, které popisují umístění instalace těchto šablon. K aktualizaci rozšíření VSIX můžete použít instalaci Preview 2. Pokud nasadíte rozšíření pomocí MSI, je nutné vygenerovat soubory manifestu šablony ručně. Další informace najdete v tématu [upgrade Custom šablony projektů a položek pro Visual Studio 2017](/visualstudio/extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017?view=vs-2015). Schéma manifestu šablony je dokumentováno v [referenčních informacích o schématu manifestu šablony sady Visual Studio](/visualstudio/extensibility/visual-studio-template-manifest-schema-reference).

## <a name="create-a-project-template"></a>Vytvoření šablony projektu

1. Vytvořte projekt šablony projektu. Šablonu projektu můžete najít v dialogovém okně **Nový projekt** , ve složce Visual Basic nebo **rozšiřitelné** složky Visual C#.

     Šablona vygeneruje soubor třídy, ikonu, soubor. vstemplate, upravitelný soubor projektu s názvem ProjectTemplate. vbproj nebo ProjectTemplate. csproj a některé soubory, které jsou obvykle generovány jinými typy projektů, jako například soubor prostředků. resx, soubor AssemblyInfo a soubor. Settings. Každý soubor kódu obsahuje v případě potřeby společné náhrady parametrů.

2. Přidejte a odeberte položky z projektu, jak je požadováno pro váš projekt. Neodstraňujte upravitelný soubor projektu, soubor AssemblyInfo nebo soubor. vstemplate.

3. Aktualizujte soubor. vstemplate tak, aby odrážel všechna přidání a odstranění. Prvek [projektu](../extensibility/project-element-visual-studio-templates.md) musí obsahovat element [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md) pro každý soubor, který se má zahrnout do šablony.

4. Upravte soubory kódu a další obsah s přístupem uživatele a přidejte odpovídající náhrady parametrů.

5. Podle potřeby upravte generovaný obsah.

6. Sestavte projekt.

     Visual Studio vytvoří soubor. zip, který obsahuje vaši šablonu. Není nasazený a není k dispozici v experimentální instanci.

## <a name="create-an-item-template"></a>Vytvoření šablony položky

1. Vytvořte projekt šablony položky.

     Šablona vygeneruje soubor třídy, ikonu, soubor. vstemplate a soubor AssemblyInfo. Soubor třídy obsahuje některé běžné náhrady parametrů.

2. Přidejte a odeberte položky z projektu, jak je požadováno pro váš projekt.

3. Aktualizujte soubor. vstemplate tak, aby odrážel všechna přidání a odstranění. Prvek [projektu](../extensibility/project-element-visual-studio-templates.md) musí obsahovat element [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md) pro každý soubor, který se má zahrnout do šablony.

4. Upravte soubory kódu a další obsah s přístupem uživatele a přidejte odpovídající náhrady parametrů.

5. Upravte vygenerovaný obsah podle potřeby.

6. Sestavte projekt.

     Visual Studio vytvoří komprimovaný soubor, který obsahuje vaši šablonu. Není nasazený a není k dispozici v experimentální instanci.

## <a name="deploy-the-project-or-item-template"></a>Nasazení šablony projektu nebo položky

1. Vytvořte projekt VSIX. Další informace naleznete v tématu [Šablona projektu VSIX](../extensibility/vsix-project-template.md).

2. Nastavte projekt VSIX jako spouštěný projekt. V **Průzkumník řešení**vyberte uzel projekt VSIX, klikněte pravým tlačítkem myši a vyberte **nastavit jako spouštěný projekt**.

3. Nastavte projekt šablony projektu jako Asset projektu VSIX. Otevřete soubor. vsixmanifest. Přejděte na kartu **assets (prostředky** ) a klikněte na **Nový**.

    1. Nastavte pole **typ** na **Microsoft. VisualStudio. ProjectTemplate** nebo **Microsoft. VisualStudio. ItemTemplate**.

    2. V části zdroj vyberte možnost **projekt v aktuální řešení** a pak vyberte projekt, který obsahuje šablonu.

4. Sestavte řešení a stiskněte klávesu F5. Objeví se experimentální instance.

5. V projektu šablony projektu by se měla zobrazit šablona projektu uvedená v dialogovém okně **Nový projekt** (**soubor/nový/projekt**) v uzlu Visual C# nebo Visual Basic. Pro projekt šablony položky by se měla zobrazit Šablona položky uvedená v dialogovém okně Přidat novou položku (v **Průzkumník řešení**vyberte uzel projektu a klikněte na **přidat/nová položka**).

## <a name="see-also"></a>Viz také

- [Referenční dokumentace šablony sady Visual Studio](../ide/visual-studio-template-reference.md)