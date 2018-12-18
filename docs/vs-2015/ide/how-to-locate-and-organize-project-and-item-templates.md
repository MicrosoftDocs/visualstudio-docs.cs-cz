---
title: 'Postupy: hledání a organizace projektů a šablon položek | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- project templates [Visual Studio], locations
- custom template locations [Visual Studio]
- item templates, locations
- Visual Studio templates, locations
- project templates [Visual Studio], displaying
- templates [Visual Studio], locations
ms.assetid: 71f9ed52-c9c9-4818-9bce-c279ffaa0438
caps.latest.revision: 28
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2a3954e5d18db6585c8dbda017773969f96b33de
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49830974"
---
# <a name="how-to-locate-and-organize-project-and-item-templates"></a>Postupy: Hledání a organizace projektů a šablon položek
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Soubory šablony musí být umístěn do umístění, které Visual Studio rozpozná tak, aby se šablony se zobrazí v **nový projekt** a **přidat novou položku** dialogových oknech. Můžete vytvořit vlastní podkategorie šablony tak, aby podkategorií se také zobrazí v uživatelském rozhraní.  
  
## <a name="locating-templates"></a>Umístění šablon  
 Ve výchozím nastavení Visual Studio vyhledá dvě umístění pro šablony projektů a položek. Pokud existuje komprimovaný soubor, který obsahuje soubor .vstemplate v těchto umístěních, šablony se zobrazí v **nový projekt** nebo **přidat novou položku** dialogových oknech.  
  
### <a name="installed-templates"></a>Nainstalované šablony  
 Ve výchozím nastavení jsou součástí šablony nainstalované společně se sadou produktu:  
  
- \\*VisualStudioInstallationDirectory*\Common7\IDE\ItemTemplates\\*jazyk*\\*národního prostředí*\  
  
- \\*VisualStudioInstallationDirectory*\Common7\IDE\ProjectTemplates\\*jazyk*\\*národního prostředí\\*  
  
  Například následující adresář obsahuje [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] šablony projektů pro angličtinu:  
  
  C:\\*VisualStudioInstallationDirectory*\Common7\IDE\ItemTemplates\VisualBasic\1033\  
  
### <a name="custom-templates"></a>Vlastní šablony  
 Ve výchozím nastavení vlastní šablony se nacházejí v:  
  
- Documents\Visual studio *verze*\Templates\ProjectTemplates\\*jazyka*\  
  
- Documents\Visual studio *verze*\Templates\ItemTemplates\\*jazyka*\  
  
  Například následující adresář obsahuje vlastní [!INCLUDE[csprcs](../includes/csprcs-md.md)] šablony projektu:  
  
  C:\Documents and Settings\UserName\My dokumenty\\< verze sady Visual Studio\>\Templates\ProjectTemplates\Visual C# \  
  
  Vlastní šablony nezahrnují podadresář pro lokalizované šablony. Můžete změnit výchozí adresář pro vlastní šablony v **možnosti** dialogovém okně **prostředí\projekty a řešení**.  
  
## <a name="organizing-templates"></a>Uspořádání šablon  
 Kategorie v **nový projekt** a **přidat novou položku** dialogová okna, aby odrážely struktury adresářů, které existují v umístění nainstalované a vlastní šablony. Tyto struktury adresářů pro uspořádání vašich šablon způsobem, který vám vyhovuje, můžete upravit.  
  
> [!NOTE]
>  Nelze vytvořit novou kategorii na úrovni programovací jazyk. Nové kategorie lze vytvořit pouze v rámci jednotlivé jazyky.  
  
 Pokud struktury adresářů pro nainstalované a vlastní šablony pro konkrétní jazyk nemají stejnou strukturu (to znamená, že existují adresáře v rámci jedné složky, které neexistují v jiné) sady kategorií, které se zobrazují v **nový Projekt** dialogové okno bude spojení všech kategorií.  
  
### <a name="organizing-installed-templates"></a>Uspořádání instalované šablony  
 Nainstalovaných šablon můžete uspořádat tak, že vytvoříte podsložky ve složce programovací jazyk. Tyto podsložky se zobrazí v **nový projekt** a **přidat novou položku** dialogová okna jako virtuální složky v rámci jednotlivé jazyky.  
  
##### <a name="to-create-new-installed-project-template-categories"></a>Vytvořit nový projekt nainstalovaných kategorie šablony  
  
1. Vytvořte složku ve složce jazyka adresář nainstalovaných šablon. Chcete-li například vytvořit kategorie Office pro [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projektu šablony, které vytvoříte v následujícím adresáři:  
  
    \\*VisualStudioInstallationDirectory*\Common7\IDE\ProjectTemplates\VisualBasic\1033\Office\  
  
2. Umístěte všechny šablony pro tuto kategorii do nové složky.  
  
3. Zavřete všechny instance [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
4. Na **Start** nabídky, klikněte na tlačítko **spustit**, typ **cmd**a klikněte na tlačítko **OK**.  
  
5. Na příkazovém řádku vyhledejte adresář, který obsahuje devenv.exe a typ **devenv/installvstemplates**.  
  
6. Spustit [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
7. Na **souboru** nabídky, klikněte na tlačítko **nový**a potom klikněte na tlačítko **projektu**.  
  
8. Ověřte, že kategorie Office se zobrazí v **nový projekt** v dialogu **typy projektů** podokně v části [!INCLUDE[vbprvb](../includes/vbprvb-md.md)].  
  
   Je také možné seskupovat podmnožinu šablony položek projektu do vlastní složky.  
  
##### <a name="to-create-new-installed-item-template-categories"></a>Vytvořit novou položku nainstalovaných kategorie šablony  
  
1.  Vytvořte složku ve složce jazyka adresář nainstalovaných šablon. Chcete-li například vytvořit kategorii Web pro [!INCLUDE[csprcs](../includes/csprcs-md.md)] položku šablony vytvoříte v následujícím adresáři:  
  
     \\*VisualStudioInstallationDirectory*\Common7\IDE\ItemTemplates\CSharp\1033\Web\  
  
2.  Umístěte všechny šablony pro tuto kategorii do nové složky.  
  
3.  Zavřete všechny instance [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
4.  Na **Start** nabídky, klikněte na tlačítko **spustit**, typ **cmd**a klikněte na tlačítko **OK**.  
  
5.  Na příkazovém řádku vyhledejte adresář, který obsahuje devenv.exe a typ **devenv/Setup**.  
  
6.  Spustit [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
7.  Vytvoření projektu nebo otevřete existující projekt.  
  
8.  Na **projektu** nabídky, klikněte na tlačítko **přidat novou položku**.  
  
9. Ověřte, že Web se zobrazí kategorie **přidat novou položku** v dialogu **typy projektů** podokně.  
  
### <a name="organizing-custom-templates"></a>Uspořádání vlastní šablony  
 Vlastní šablony lze uspořádat do své vlastní kategorie tak, že přidáte nové složky v umístění vlastních šablon. **Nový projekt** dialogové okno odráží všechny změny provedené v kategorie šablony.  
  
##### <a name="to-create-new-custom-project-template-categories"></a>Chcete-li vytvořit nový vlastní projekt kategorií šablon  
  
1. Vytvoření složky v jazykovou složku v adresáři projektu vlastní šablony. Například pro vytvoření kategorie HelloWorld [!INCLUDE[csprcs](../includes/csprcs-md.md)] šablony, vytvořili byste následující adresář:  
  
    Dokumenty \My\\< verze sady Visual Studio\>\Templates\ProjectTemplates\CSharp\HelloWorld\  
  
2. Umístěte všechny šablony pro tuto kategorii do nové složky.  
  
3. Na **souboru** nabídky, klikněte na tlačítko **nový**a potom klikněte na tlačítko **projektu**.  
  
4. Ověřte, že se zobrazí kategorie HelloWorld v **nový projekt** v dialogu **typy projektů** podokně v části [!INCLUDE[csprcs](../includes/csprcs-md.md)].  
  
   Je také možné seskupovat podmnožinu vlastních šablon položek do vlastní složky.  
  
##### <a name="to-create-new-custom-item-template-categories"></a>Chcete-li vytvořit nové vlastní položky kategorií šablon  
  
1.  Vytvořte složku ve složce jazyka v adresáři vlastní položky šablon. Například pro vytvoření kategorie HelloWorld [!INCLUDE[csprcs](../includes/csprcs-md.md)] šablony vytvoříte v následujícím adresáři:  
  
     Dokumenty \My\\< verze sady Visual Studio\>\Templates\ItemTemplates\CSharp\HelloWorld\  
  
2.  Umístěte všechny šablony pro tuto kategorii do nové složky.  
  
3.  Vytvoření projektu nebo otevřete existující projekt.  
  
4.  Na **projektu** nabídky, klikněte na tlačítko **přidat novou položku**.  
  
5.  Ověřte, že se zobrazí kategorie HelloWorld v **přidat novou položku** v dialogu **typy projektů** podokně.  
  
### <a name="displaying-templates-in-parent-categories"></a>Zobrazení šablony v nadřazené kategorie  
 Můžete povolit v podkategoriích, který se má zobrazit v jejich nadřazené kategorie pomocí šablony `NumberOfParentCategoriesToRollUp` element v souboru .vstemplate. Tyto postupy jsou stejné pro šablony projektů a šablon položek.  
  
##### <a name="to-display-templates-in-parent-categories"></a>Chcete-li zobrazit šablony v nadřazené kategorie  
  
1.  Vyhledejte soubor .zip, který obsahuje šablonu.  
  
2.  Extrahujte soubor ZIP.  
  
3.  Otevřete soubor .vstemplate v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
4.  V `TemplateData` elementu, přidejte `NumberOfParentCategoriesToRollUp` elementu. Například následující kód vytvoří šablonu viditelné v nadřazené kategorie, ale ne vyšší.  
  
    ```  
    <TemplateData>  
        ...  
        <NumberOfParentCategoriesToRollUp>  
            1  
        </NumberOfParentCategoriesToRollUp>  
        ...  
    </TemplateData>  
    ```  
  
5.  Uložte a zavřete soubor .vstemplate.  
  
6.  Vyberte soubory do šablony, klikněte pravým tlačítkem na výběr, klikněte na tlačítko **odeslat**a potom klikněte na tlačítko **komprimovaná složka (metoda ZIP)**. Soubory jsou komprimována do souboru .zip.  
  
7.  Odstraňte extrahované soubory šablony a starý soubor ZIP šablony.  
  
8.  Vložte nový soubor ZIP do adresáře, který měl odstraněný .zip soubor.  
  
## <a name="see-also"></a>Viz také  
 [Přizpůsobení šablon](../ide/customizing-project-and-item-templates.md)   
 [Odkaz na schéma šablon sady Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [NumberOfParentCategoriesToRollUp (šablony sady Visual Studio)](../extensibility/numberofparentcategoriestorollup-visual-studio-templates.md)   
 [Postupy: vytváření šablon projektu](../ide/how-to-create-project-templates.md)   
 [Postupy: Vytváření šablon položek](../ide/how-to-create-item-templates.md)



