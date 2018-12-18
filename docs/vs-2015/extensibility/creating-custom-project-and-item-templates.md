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
manager: douge
ms.openlocfilehash: 88b4ffb717b8009b7fe2478ab38070ccf11dd169
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53065045"
---
# <a name="creating-custom-project-and-item-templates"></a>Vytváření vlastních šablon projektů a položek
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio SDK zahrnuje šablony projektu, které vytvořit vlastní šablonu projektu a šablonu vlastní položky. Tyto šablony zahrnují některých běžných náhrad parametrů a sestavení jako soubory zip. Nejsou nasazeni automaticky a nejsou k dispozici v experimentální instanci aplikace. Kopírování souboru zip soubor do umístění

Vytvoření šablony šablony umožňují zahrnout šablony do větších rozšíření. Včetně šablon v rozšíření umožňuje implementaci správy verzí na zdrojové soubory a vytvořit skupinu šablony projektů do jednoho balíčku VSIX.

Pro scénáře vytvoření základní šablony, byste měli použít **exportovat šablonu** průvodce, který uloží do komprimovaného souboru. Další informace o vytvoření základní šablony najdete v tématu [vytváření projektů a šablon položek](../ide/creating-project-and-item-templates.md).

Spouští se v sadě Visual Studio 2017, vyhledávání vlastních projektů a šablon položek už probíhá. Rozšíření místo toho musíte zadat soubory manifestu šablon, které popisují umístění instalace služby tyto šablony. Instalace Preview 2 můžete použít k aktualizaci rozšíření VSIX. Pokud provádíte nasazení vašeho rozšíření pomocí MSI, musíte soubory manifestu šablony vygenerovat ručně. Další informace najdete v tématu [Upgrade vlastních šablon projektů a položek pro Visual Studio 2017](/visualstudio/extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017?view=vs-2015). Schéma manifestu šablony je popsána v [Visual Studio Manifest odkaz na schéma šablon](/visualstudio/extensibility/visual-studio-template-manifest-schema-reference).

## <a name="create-a-project-template"></a>Vytvoření šablony projektu

1.  Vytvořte projekt šablony projektu. Můžete najít šablonu projektu v **nový projekt** dialogového okna, v jazyce Visual Basic nebo Visual C# **rozšiřitelnost** složky.

     Tato šablona vygeneruje soubor třídy, ikony, soubor .vstemplate, soubor upravovat projektu s názvem ProjectTemplate.vbproj nebo ProjectTemplate.csproj a některé soubory, které jsou obvykle generovány jinými typy projektů, takový resources.resx soubor, AssemblyInfo soubor a soubor .settings. Každý soubor kódu obsahuje běžné náhrad parametrů, kde je to vhodné.

2.  Přidání a odebrání položek z projektu, jak je vyžadováno pro váš projekt. Neodebírejte soubor upravovat projektu, souboru AssemblyInfo nebo souboru .vstemplate.

3.  Aktualizujte soubor .vstemplate tak, aby odrážela všechny přidání a odstranění. [Projektu](../extensibility/project-element-visual-studio-templates.md) musí obsahovat element [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md) – element pro každý soubor mají být zahrnuty v šabloně.

4.  Upravit soubory kódu a další obsah přístupných a přidejte odpovídající parametr nahrazení.

5.  Upravte vygenerovaný obsah podle potřeby.

6.  Sestavte projekt.

     Visual Studio vytvoří soubor .zip, který obsahuje šablonu. Není nasazená, a není k dispozici v experimentální instanci aplikace.

## <a name="create-an-item-template"></a>Vytvořit šablonu položky

1.  Vytvoření šablony položky projektu.

     Tato šablona vygeneruje soubor třídy, ikony, soubor .vstemplate a souboru AssemblyInfo. Soubor třídy obsahuje některé běžné náhrad parametrů.

2.  Přidání a odebrání položek z projektu, jak je vyžadováno pro váš projekt.

3.  Aktualizujte soubor .vstemplate tak, aby odrážela všechny přidání a odstranění. [Projektu](../extensibility/project-element-visual-studio-templates.md) musí obsahovat element [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md) – element pro každý soubor mají být zahrnuty v šabloně.

4.  Upravit soubory kódu a další obsah přístupných a přidejte odpovídající parametr nahrazení.

5.  Upravte vygenerovaný obsah podle potřeby.

6.  Sestavte projekt.

     Visual Studio vytvoří komprimovaný soubor, který obsahuje šablonu. Není nasazená, a není k dispozici v experimentální instanci aplikace.

## <a name="deploy-the-project-or-item-template"></a>Nasazení šablony projektu nebo položky

1.  Vytvořte projekt VSIX. Další informace najdete v tématu [šablonou projektu VSIX](../extensibility/vsix-project-template.md).

2.  Nastavte projekt VSIX jako projekt po spuštění. V **Průzkumníka řešení**, vyberte uzel projektu VSIX, klikněte pravým tlačítkem a vyberte **nastavit jako spouštěný projekt**.

3.  Nastavte projekt šablony projektu jako prostředek projektu VSIX. Otevřete soubor .vsixmanifest. Přejděte **prostředky** kartě a klikněte na tlačítko **nový**.

    1.  Nastavte **typ** pole **Microsoft.VisualStudio.ProjectTemplate** nebo **Microsoft.VisualStudio.ItemTemplate**.

    2.  Pro zdroj, vyberte **projekt v aktuálním řešení** možnost a potom vyberte projekt, který obsahuje šablonu.

4.  Sestavte řešení a stiskněte klávesu F5. Zobrazí se experimentální instance.

5.  Pro projekt šablony projektu, byste měli vidět vaše šablona projektu uvedené v **nový projekt** dialogového okna (**soubor / nový / Project**), Visual C# nebo Visual Basic uzlu. Pro projekt šablony položky, měli byste vidět položku šablony uvedené v dialogovém okně Přidat novou položku (v **Průzkumníka řešení**, vyberte uzel projektu a klikněte na tlačítko **Add / nová položka**).

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace šablony sady Visual Studio](../ide/visual-studio-template-reference.md)