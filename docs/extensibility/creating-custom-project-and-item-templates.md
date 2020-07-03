---
title: Vytváření vlastních šablon projektů a položek | Microsoft Docs
ms.date: 3/16/2019
ms.topic: overview
ms.assetid: 586da5dc-f678-402b-afd0-0332959fd7a6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5c702aaaa51d86e2b8aac18a6b55201be03a635f
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2020
ms.locfileid: "85903322"
---
# <a name="create-custom-project-and-item-templates"></a>Vytváření vlastních šablon projektů a položek

Sada Visual Studio SDK obsahuje šablony projektu, které vytvoří vlastní šablonu projektu a šablonu vlastní položky. Tyto šablony obsahují některé běžné náhrady parametrů a sestavování jako soubory zip. Nejsou nasazeny automaticky a nejsou k dispozici v experimentální instanci. Vygenerovaný soubor ZIP je nutné zkopírovat do adresáře šablon uživatele.

Šablony pro vytváření šablon umožňují zahrnout šablony do větších rozšíření. To umožňuje implementovat řízení verze ve zdrojových souborech a vytvořit skupinu projektů šablon do jednoho balíčku VSIX.

Můžete také nakonfigurovat šablonu pro instalaci balíčků NuGet. Další informace najdete v tématu [balíčky NuGet v šablonách sady Visual Studio](/nuget/visual-studio-extensibility/visual-studio-templates).

V případě scénářů pro základní vytváření šablon byste měli použít průvodce **exportem šablony** , který vrací výstup do komprimovaného souboru. Další informace o vytváření základních šablon naleznete v tématu [vytváření šablon projektů a položek](../ide/creating-project-and-item-templates.md).

> [!NOTE]
> Počínaje verzí sady Visual Studio 2017 již nebude vyhledávání vlastních šablon projektů a položek provedeno. Místo toho musí rozšíření poskytnout soubory manifestu šablony, které popisují umístění instalace těchto šablon. Pomocí sady Visual Studio 2017 můžete aktualizovat rozšíření VSIX. Pokud nasadíte rozšíření pomocí MSI, je nutné vygenerovat soubory manifestu šablony ručně. Další informace naleznete v tématu [Upgrade vlastních šablon projektů a položek pro Visual Studio 2017](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md). Schéma manifestu šablony je dokumentováno v [referenčních informacích o schématu manifestu šablony sady Visual Studio](../extensibility/visual-studio-template-manifest-schema-reference.md).

## <a name="create-a-project-template"></a>Vytvoření šablony projektu

1. Vytvořte projekt šablony projektu. Šablonu projektu najdete v dialogovém okně **Nový projekt** , a to tak, že vyhledáte "šablona projektu" a vyberete buď verzi C# nebo Visual Basic.

     Šablona vygeneruje soubor třídy, ikonu, soubor *. vstemplate* , upravitelný soubor projektu s názvem *ProjectTemplate. vbproj* nebo *ProjectTemplate. csproj*a některé soubory, které jsou obvykle generovány jinými typy projektů, jako například soubor *prostředků. resx* , soubor *AssemblyInfo* a soubor *. Settings* . Každý soubor kódu obsahuje v případě potřeby společné náhrady parametrů.

![výběr projektu šablony projektu](media/project-template-selection.png)

2. Přidejte a odeberte položky z projektu, jak je požadováno pro váš projekt. Neodstraňujte upravitelný soubor projektu, soubor *AssemblyInfo* nebo soubor *. vstemplate* .

3. Aktualizujte soubor *. vstemplate* tak, aby odrážel všechna přidání a odstranění. Prvek [projektu](../extensibility/project-element-visual-studio-templates.md) musí obsahovat element [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md) pro každý soubor, který se má zahrnout do šablony.

4. Upravte soubory kódu a další obsah s přístupem uživatele a přidejte odpovídající náhrady parametrů.

5. Podle potřeby upravte generovaný obsah.

6. Sestavte projekt.

     Visual Studio vytvoří soubor *. zip* , který obsahuje vaši šablonu. Není nasazený a není k dispozici v experimentální instanci.

## <a name="create-an-item-template"></a>Vytvoření šablony položky

1. Vytvořte projekt šablony položky.

     Šablona vygeneruje soubor třídy, ikonu, soubor *. vstemplate* a soubor *AssemblyInfo* . Soubor třídy obsahuje některé běžné náhrady parametrů.

2. Přidejte a odeberte položky z projektu, jak je požadováno pro váš projekt.

3. Aktualizujte soubor *. vstemplate* tak, aby odrážel všechna přidání a odstranění. Prvek [projektu](../extensibility/project-element-visual-studio-templates.md) musí obsahovat element [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md) pro každý soubor, který se má zahrnout do šablony.

4. Upravte soubory kódu a další obsah s přístupem uživatele a přidejte odpovídající náhrady parametrů.

5. Upravte vygenerovaný obsah podle potřeby.

6. Sestavte projekt.

     Visual Studio vytvoří komprimovaný soubor, který obsahuje vaši šablonu. Není nasazený a není k dispozici v experimentální instanci.

## <a name="deployment"></a>Nasazení

### <a name="to-deploy-the-project-or-item-template"></a>Nasazení šablony projektu nebo položky

1. Vytvořte projekt VSIX. Další informace naleznete v tématu [Šablona projektu VSIX](../extensibility/vsix-project-template.md).

2. Nastavte projekt VSIX jako spouštěný projekt. V **Průzkumník řešení**vyberte uzel projekt VSIX, klikněte pravým tlačítkem myši a vyberte **nastavit jako spouštěný projekt**.

3. Nastavte projekt šablony projektu jako Asset projektu VSIX. Otevřete soubor *. vsixmanifest* . Přejděte na kartu **assets (prostředky** ) a klikněte na **Nový**.

    1. Nastavte pole **typ** na **Microsoft. VisualStudio. ProjectTemplate** nebo **Microsoft. VisualStudio. ItemTemplate**.

    2. V části zdroj vyberte možnost **projekt v aktuální řešení** a pak vyberte projekt, který obsahuje šablonu.

4. Sestavte řešení a stiskněte klávesu **F5**. Objeví se experimentální instance.

5. V projektu šablony projektu by se měla zobrazit šablona projektu uvedená v dialogovém okně **Nový projekt** (**soubor**  >  **Nový**  >  **projekt**) v uzlu Visual C# nebo Visual Basic. Pro projekt šablony položky by se měla zobrazit Šablona položky uvedená v dialogovém okně **Přidat novou položku** . Chcete-li zobrazit dialogové okno **Přidat novou položku** , vyberte z **Průzkumník řešení**uzel projektu a klikněte na tlačítko **Přidat**  >  **novou položku**).

## <a name="see-also"></a>Viz také

- [Referenční dokumentace šablony sady Visual Studio](../ide/creating-project-and-item-templates.md)
- [Balíčky NuGet v šablonách sady Visual Studio](/nuget/visual-studio-extensibility/visual-studio-templates)
