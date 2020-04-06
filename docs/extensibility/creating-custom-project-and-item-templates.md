---
title: Vytváření vlastních šablon projektů a položek | Dokumenty společnosti Microsoft
ms.date: 3/16/2019
ms.topic: conceptual
ms.assetid: 586da5dc-f678-402b-afd0-0332959fd7a6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ae404004f2660048ef7581a661d8f785495ed95a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739454"
---
# <a name="create-custom-project-and-item-templates"></a>Vytvoření vlastních šablon projektů a položek

Sada Visual Studio SDK obsahuje šablony projektů, které vytvářejí vlastní šablonu projektu a vlastní šablonu položky. Tyto šablony obsahují některé běžné náhrady parametrů a sestavení jako soubory zip. Nejsou automaticky nasazeny a nejsou k dispozici v experimentální instanci. Vygenerovaný soubor ZIP je nutné zkopírovat do adresáře šablony uživatele.

Šablony pro vytváření šablon umožňují zahrnout šablony do větších rozšíření. To vám umožní implementovat správu verzí na zdrojové soubory a vytvořit skupinu projektů šablon do jednoho balíčku VSIX.

Můžete také nakonfigurovat šablonu pro instalaci balíčků NuGet. Další informace naleznete [v tématu Balíčky NuGet v šablonách sady Visual Studio](/nuget/visual-studio-extensibility/visual-studio-templates).

Pro základní scénáře vytváření šablon byste měli použít Průvodce **exportem šablony,** který se vyváží do komprimovaného souboru. Další informace o vytváření základních šablon naleznete v [tématu Vytváření šablon projektu a položek](../ide/creating-project-and-item-templates.md).

> [!NOTE]
> Počínaje Visual Studio 2017, hledání vlastních šablon projektů a položek již nebude provedeno. Místo toho rozšíření musí poskytnout soubory manifestu šablony, které popisují umístění instalace těchto šablon. Pomocí Visual Studia 2017 můžete aktualizovat rozšíření VSIX. Pokud nasadíte rozšíření pomocí MSI, musíte vygenerovat soubory manifestu šablony ručně. Další informace naleznete v [tématu Upgrade vlastních šablon projektů a položek pro Visual Studio 2017](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md). Schéma manifestu šablony je popsáno v odkazu na schéma [manifestu šablony sady Visual Studio](../extensibility/visual-studio-template-manifest-schema-reference.md).

## <a name="create-a-project-template"></a>Vytvoření šablony projektu

1. Vytvořte projekt šablony projektu. Šablonu projektu najdete v dialogovém okně **Nový projekt** vyhledáním "šablony projektu" a výběrem verze jazyka C# nebo Visual Basic.

     Šablona generuje soubor třídy, ikonu, soubor *.vstemplate,* upravitelný soubor projektu s názvem *ProjectTemplate.vbproj* nebo *ProjectTemplate.csproj*a některé soubory, které jsou obvykle generovány jinými typy projektů, například *souborem resources.resx,* souborem *AssemblyInfo* a souborem *.settings.* Každý soubor kódu obsahuje běžné nahrazení parametrů, kde je to vhodné.

![výběr projektu šablony](media/project-template-selection.png)

2. Přidejte a odeberte položky z projektu podle potřeby pro váš projekt. Neodstraňujte upravitelný soubor projektu, soubor *AssemblyInfo* ani soubor *.vstemplate.*

3. Aktualizujte soubor *.vstemplate* tak, aby odrážel všechny dodatky a odstranění. [Prvek Project](../extensibility/project-element-visual-studio-templates.md) musí obsahovat prvek [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md) pro každý soubor, který má být zahrnut do šablony.

4. Upravte soubory kódu a další obsah orientovaný na uživatele a přidejte příslušné náhrady parametrů.

5. Podle potřeby upravte generovaný obsah.

6. Sestavte projekt.

     Visual Studio vytvoří soubor *ZIP,* který obsahuje vaši šablonu. Není nasazena a není k dispozici v experimentální instanci.

## <a name="create-an-item-template"></a>Vytvoření šablony položky

1. Vytvořte projekt šablony položky.

     Šablona vygeneruje soubor třídy, ikonu, soubor *.vstemplate* a soubor *AssemblyInfo.* Soubor třídy obsahuje některé běžné nahrazení parametrů.

2. Přidejte a odeberte položky z projektu podle potřeby pro váš projekt.

3. Aktualizujte soubor *.vstemplate* tak, aby odrážel všechny dodatky a odstranění. [Prvek Project](../extensibility/project-element-visual-studio-templates.md) musí obsahovat prvek [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md) pro každý soubor, který má být zahrnut do šablony.

4. Upravte soubory kódu a další obsah orientovaný na uživatele a přidejte příslušné náhrady parametrů.

5. Podle potřeby upravte generovaný obsah.

6. Sestavte projekt.

     Visual Studio vytvoří komprimovaný soubor, který obsahuje vaši šablonu. Není nasazena a není k dispozici v experimentální instanci.

## <a name="deployment"></a>Nasazení

### <a name="to-deploy-the-project-or-item-template"></a>Nasazení šablony projektu nebo položky

1. Vytvořte projekt VSIX. Další informace naleznete [v tématu Šablona projektu VSIX](../extensibility/vsix-project-template.md).

2. Nastavte projekt VSIX jako projekt spuštění. V **Průzkumníku řešení**vyberte uzel projektu VSIX, klepněte pravým tlačítkem myši a vyberte **nastavit jako spouštěcí projekt**.

3. Nastavte projekt šablony projektu jako datový zdroj projektu VSIX. Otevřete soubor *.vsixmanifest.* Přejděte na kartu **Datové zdroje** a klepněte na **tlačítko Nový**.

    1. Nastavte pole **Typ** na **Microsoft.VisualStudio.ProjectTemplate** nebo **Microsoft.VisualStudio.ItemTemplate**.

    2. Pro zdroj vyberte **možnost A projekt v aktuálním řešení** a vyberte projekt, který obsahuje šablonu.

4. Sestavte řešení a stiskněte **klávesu F5**. Zobrazí se experimentální instance.

5. U projektu šablony projektu byste měli vidět šablonu projektu uvedenou v dialogovém okně **Nový projekt** **(Soubor** > **nového** > **projektu**) v uzlu Visual C# nebo Visual Basic. U projektu šablony položky byste měli vidět šablonu položky uvedenou v dialogovém okně **Přidat novou položku.** Chcete-li zobrazit dialogové okno **Přidat novou položku,** vyberte v **Průzkumníku řešení**uzel projektu a klepněte na tlačítko **Přidat** > **novou položku**).

## <a name="see-also"></a>Viz také

- [Odkaz na šablonu sady Visual Studio](../ide/creating-project-and-item-templates.md)
- [Balíčky NuGet v šablonách sady Visual Studio](/nuget/visual-studio-extensibility/visual-studio-templates)
