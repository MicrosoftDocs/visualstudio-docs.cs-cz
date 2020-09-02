---
title: 'Postupy: Aktualizace existujících šablon | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- item templates, updating existing templates
- Visual Studio templates, updating existing templates
- project templates, updating existing templates
ms.assetid: d585e45b-7fe2-45fa-9cf3-7f2bc060f3c4
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4b56cf11057957b0eb99fc065ed26af10d8adfbd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670575"
---
# <a name="how-to-update-existing-templates"></a>Postupy: Aktualizace existujících šablon
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Po vytvoření šablony a komprimaci souborů do souboru s příponou. zip budete možná chtít šablonu upravit. To můžete provést ručně změnou souborů v šabloně nebo exportováním nové šablony z projektu, který je založen na šabloně.

## <a name="using-the-export-template-wizard-to-update-an-existing-template"></a>Aktualizace existující šablony pomocí Průvodce exportem šablony
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] poskytuje průvodce **exportem šablony** , který lze použít k aktualizaci existující šablony.

#### <a name="to-use-export-template-to-update-an-existing-template"></a>Použití šablony pro export k aktualizaci existující šablony

1. V nabídce **soubor** klikněte na příkaz **Nový** a potom klikněte na **Nový projekt**.

2. Vyberte šablonu, kterou chcete aktualizovat, zadejte název a umístění pro dočasný projekt a klikněte na tlačítko **OK**.

3. Upravte projekt v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

4. V nabídce **soubor** klikněte na položku **Exportovat šablonu**a pomocí průvodce **exportem šablony** vytvořte novou šablonu.

5. Po komprimaci aktualizované šablony do souboru. zip odstraňte starý soubor Template. zip.

## <a name="manually-updating-an-existing-template"></a>Ruční aktualizace stávající šablony
 Existující šablonu můžete aktualizovat mimo [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] úpravu souborů v komprimovaném souboru ZIP.

#### <a name="to-manually-update-an-existing-template"></a>Ruční aktualizace stávající šablony

1. Vyhledejte soubor. zip, který obsahuje šablonu. Ve výchozím nastavení se tento soubor nachází ve složce \My Documents\Visual Studio *verze*\My Exported Templates \\ .

2. Extrahujte soubor. zip.

3. Upravte nebo odstraňte aktuální soubory šablon nebo přidejte nové soubory do šablony.

4. Otevřete, upravte a uložte soubor XML. vstemplate pro zpracování aktualizovaných chování nebo nových souborů. Další informace o schématu. vstemplate naleznete v tématu [Referenční dokumentace schématu šablon sady Visual Studio](../extensibility/visual-studio-template-schema-reference.md). Další informace o tom, co můžete ve zdrojových souborech parametrizovat, najdete v tématu [parametry šablony](../ide/template-parameters.md) .

5. Vyberte soubory v šabloně, klikněte pravým tlačítkem myši, klikněte na **Odeslat do**a pak klikněte na **komprimovanou složku (ZIP)**. Soubory, které jste vybrali, se komprimují do souboru ZIP.

6. Vložte nový soubor. zip do stejného adresáře jako starý soubor. zip.

7. Odstraňte extrahované soubory šablon a starý soubor Template. zip.

8. Spusťte (jako správce) instanci Developer Command Prompt (v nabídce Start v části **Visual Studio 2010/Visual Studio Tools/Developer Command Prompt**).

9. Spusťte následující příkaz: `devenv /installvstemplates` .

## <a name="see-also"></a>Viz také
 [Přizpůsobení šablon](../ide/customizing-project-and-item-templates.md) [Vytvoření šablon projektů a položek](../ide/creating-project-and-item-templates.md) [referenční šablona schématu šablon sady Visual Studio referenční](../extensibility/visual-studio-template-schema-reference.md) [Template Parameters](../ide/template-parameters.md) [informace k: Vytváření startovních sad](../ide/how-to-create-starter-kits.md)
