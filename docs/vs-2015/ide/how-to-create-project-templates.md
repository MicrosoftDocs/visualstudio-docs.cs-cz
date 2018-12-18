---
title: 'Postupy: vytváření šablon projektu | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
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
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: fb68a9902fc3adf9f2643b52e069cf182d9ca75a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49225506"
---
# <a name="how-to-create-project-templates"></a>Postupy: Vytváření šablon projektu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tento postup umožňuje vytvořit pomocí šablony **exportovat šablonu** průvodce, který zabalí vaše šablony v souboru .zip. Můžete také vytvořit šablony ve formátu souboru VSIX pro vylepšené nasazení s použitím Průvodce exportem šablony rozšíření nebo pomocí šablon, které jsou součástí [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)], nebo můžete vytvořit šablony ručně.  
  
### <a name="to-create-a-custom-project-template-with-the-standard-export-template-wizard"></a>Chcete-li vytvořit vlastní šablonu projektu pomocí standardního Průvodce exportovat šablonu  
  
1.  Vytvoření projektu.  
  
    > [!NOTE]
    >  Při pojmenování projektu, který bude sloužit jako zdroj šablony, používejte pouze znaky platný identifikátor. Šablonu exportovat z projektu s názvem se neplatné znaky. mohou způsobit chyby kompilace v budoucnu projekty založené na šabloně. Další informace o platný identifikátor znaků naleznete v tématu [deklarované názvy elementů](http://msdn.microsoft.com/library/09d8843b-c0dc-4afe-9dab-87c439a69e66).  
  
2.  Upravte projekt, dokud nebude připravený exportovat jako šablonu.  
  
3.  Podle potřeby upravte soubory kódu k označení, kde by měla probíhat náhrada parametru. Další informace o nahrazení parametru najdete v tématu [jak: náhradní parametry v šabloně](../ide/how-to-substitute-parameters-in-a-template.md).  
  
4.  Na **souboru** nabídky, klikněte na tlačítko **exportovat šablonu**. **Exportovat šablonu** otevře se průvodce.  
  
5.  Klikněte na tlačítko **projektu šablony**.  
  
6.  Pokud máte více než jeden projekt v aktuálním řešení, vyberte projekty, které chcete exportovat do šablony.  
  
7.  Klikněte na tlačítko **Další**.  
  
8.  Vyberte ikonu a image ve verzi preview pro šablonu. Zobrazí **nový projekt** dialogové okno.  
  
9. Zadejte název šablony a popis.  
  
10. Klikněte na tlačítko **Dokončit**. Váš projekt je exportovali do souboru ZIP a umístí do zadané výstupní umístění a k importu do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
     Pokud máte [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] nainstalované, můžete zabalit dokončená šablona v souboru VSIX pro nasazení s použitím **projekt VSIX** šablony. Další informace najdete v tématu [Začínáme s šablonou projektu VSIX](../extensibility/getting-started-with-the-vsix-project-template.md).  
  
## <a name="see-also"></a>Viz také  
 [Vytváření šablon projektů a položek](../ide/creating-project-and-item-templates.md)   
 [Postupy: Vytváření šablon položek](../ide/how-to-create-item-templates.md)



