---
title: 'Postupy: ruční vytvoření webových šablon | Dokumentace Microsoftu'
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
- Visual Studio templates, Web
- templates [Visual Studio], Web
- Web templates [Visual Studio]
- project templates [Visual Studio], Web
ms.assetid: 731c4027-a152-48c5-bfc4-93490bf1949f
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 23d810c6bbb460f01528d5f9fb55bb8ca482e383
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49880751"
---
# <a name="how-to-manually-create-web-templates"></a>Postupy: Ruční vytvoření webových šablon
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vytvoření šablony webu se liší od vytvoření jiných typů šablon. Protože joinkind šablony webových projektů **přidat nový web** dialogové okno a webové položky projektu jsou zařazené do kategorií podle programovacího jazyka, soubor .vstemplate musí určit, která šablona jako šablonu a identifikovat programování jazyk.  
  
> [!NOTE]
>  Webové šablony musí obsahovat prázdný .webproj soubor, který je určen pomocí `File` atribut `Project` elementu. I když soubory projektu nevyžadují žádné webové projekty, tento soubor je potřeba Web šablona funguje správně.  
  
### <a name="to-manually-create-a-web-template"></a>Ruční vytvoření webových šablon  
  
1. Vytvoření webového projektu.  
  
2. Upravit nebo odstranit soubory v projektu nebo přidejte nové soubory do projektu.  
  
3. Vytvořte soubor XML a uložit pomocí příponu názvu souboru .vstemplate ve stejném adresáři jako váš projekt. Nepřidávejte jej do projektu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
4. Autor XML souboru .vstemplate k poskytování metadat šablony projektu. Další informace podívejte se na příklad v následující části.  
  
5. Vyhledejte `ProjectType` prvku v souboru .vstemplate a nastavte hodnotu na text `Web`.  
  
6. Následující `ProjectType` elementu, přidejte `ProjectSubType` elementu a nastaví hodnotu text pro programovací jazyk šablony. Programovací jazyk může být jeden z následujících hodnot:  
  
   - CSharp  
  
   - VisualBasic  
  
     Příklad:  
  
   ```  
   <TemplateData>  
       ...  
       <ProjectType>Web</ProjectType>  
       <ProjectSubType>CSharp</ProjectSubType>  
       ...  
   </TemplateData>  
   ```  
  
7. Vyberte soubory v šabloně (to zahrnuje soubor .vstemplate), klikněte pravým tlačítkem na výběr, klikněte na tlačítko **odeslat**a potom klikněte na tlačítko **komprimovaná složka (metoda ZIP)**. Soubory jsou komprimována do souboru .zip.  
  
8. Vložit soubor ZIP šablony [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] adresář šablon projektu. Ve výchozím nastavení je tento adresář Documents\Visual Studio *verze*\My exportované šablony\\.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje soubor .vstemplate základní pro Šablona webového projektu.  
  
```  
<VSTemplate Version="2.0.0" Type="Project"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">>  
    <TemplateData>  
        <Name>MyWebProjecStarterKit</Name>  
        <Description>A simple Web template</Description>  
        <Icon>icon.ico</Icon>  
        <ProjectType>Web</ProjectType>  
        <ProjectSubType>CSharp</ProjectSubType>  
        <DefaultName>WebSite</DefaultName>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="WebApplication.webproj">  
            <ProjectItem>icon.ico</ProjectItem>  
            <ProjectItem OpenInEditor="true">Default.aspx</ProjectItem>  
            <ProjectItem>Default.aspx.cs</ProjectItem>  
        </Project>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>Viz také  
 [Vytváření šablon projektů a položek](../ide/creating-project-and-item-templates.md)   
 [Odkaz na schéma šablon sady Visual Studio](../extensibility/visual-studio-template-schema-reference.md)



