---
title: 'Postupy: vytváření šablon projektů | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- VS.ExportTemplateWizard
helpviewer_keywords:
- Visual Studio templates, creating project templates
- project templates, metadata files
- Visual Studio templates, project templates
- project templates, custom template locations
- project templates, creating
ms.assetid: a1a6999d-a34c-48a8-b1cf-027eb5c76398
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f358d5b95349fe99b2a2e01df5158d2c0aa10a11
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668051"
---
# <a name="how-to-create-project-templates"></a>Postupy: Vytváření šablon projektu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tento postup umožňuje vytvořit šablonu pomocí průvodce **exportem šablony** , který zabalí šablonu do souboru. zip. Můžete také vytvořit šablony ve formátu souboru VSIX pro vylepšené nasazení pomocí rozšíření Průvodce exportem šablony nebo šablonami, které jsou součástí [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)], nebo můžete vytvořit šablony ručně.

### <a name="to-create-a-custom-project-template-with-the-standard-export-template-wizard"></a>Vytvoření vlastní šablony projektu pomocí Průvodce standardní šablonou exportu

1. Vytvořte projekt.

    > [!NOTE]
    > Při pojmenování projektu, který bude zdrojem pro šablonu, použijte pouze platné znaky identifikátoru. Šablona exportovaná z projektu s názvem s neplatnými znaky může způsobit chyby kompilace v budoucích projektech na základě šablony. Další informace o platných znacích identifikátorů naleznete v tématu [deklarované názvy elementů](https://msdn.microsoft.com/library/09d8843b-c0dc-4afe-9dab-87c439a69e66).

2. Upravte projekt, dokud nebude připravený k exportu jako šablony.

3. V případě potřeby upravte soubory kódu tak, aby označovaly, kde by mělo dojít k nahrazení parametru. Další informace o nahrazení parametru naleznete v tématu [How to: dosadit Parameters in a Template](../ide/how-to-substitute-parameters-in-a-template.md).

4. V nabídce **soubor** klikněte na položku **Exportovat šablonu**. Otevře se průvodce **exportem šablony** .

5. Klikněte na **Šablona projektu**.

6. Pokud máte ve svém aktuálním řešení více než jeden projekt, vyberte projekty, které chcete exportovat do šablony.

7. Klikněte na tlačítko **Další**.

8. Vyberte ikonu a náhled obrázku pro šablonu. Ty se zobrazí v dialogovém okně **Nový projekt** .

9. Zadejte název šablony a popis.

10. Klikněte na tlačítko **Dokončit**. Projekt je exportován do souboru. zip a umístěn do zadaného umístění výstupu a v případě, že je vybrán, importován do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

     Pokud máte nainstalován [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)], můžete dokončit šablonu v souboru. VSIX pro nasazení pomocí šablony **projektu VSIX** . Další informace naleznete v tématu [Začínáme se šablonou projektu VSIX](../extensibility/getting-started-with-the-vsix-project-template.md).

## <a name="see-also"></a>Viz také
 [Vytváření šablon projektů a položek](../ide/creating-project-and-item-templates.md) [Postupy: vytváření šablon položek](../ide/how-to-create-item-templates.md)
