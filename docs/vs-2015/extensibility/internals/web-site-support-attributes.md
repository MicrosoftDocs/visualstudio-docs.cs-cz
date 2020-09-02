---
title: Atributy podpory webu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- web site projects, registration
ms.assetid: 46d52e2c-ca2a-4bbd-8500-5b0129768aec
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 75401eb0d5acd5d363d05aec57909eef5b9855e3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68144300"
---
# <a name="web-site-support-attributes"></a>Atributy podpory webu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Webový projekt lze rozšířit tak, aby poskytoval podporu webových programovacích jazyků. Jazyk se musí zaregistrovat [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , aby se šablony projektu mohly zobrazit v dialogovém okně **Nový web** , když je vybraný jazyk.  
  
 Ukázka Ironpythonu studia zahrnuje podporu webu. Můžete ji najít pomocí [ukázek VSSDK](../../misc/vssdk-samples.md). Obsahuje následující třídy atributů k registraci Ironpythonu jako jazyk CodeBehind pro nové webové projekty.  
  
## <a name="websiteprojectattribute"></a>WebSiteProjectAttribute  
 Tento atribut je umístěn v projektu jazyka. Přidá jazyk do seznamu jazyků webového programování v seznamu **jazyk** v dialogovém okně **Nový web** . Například následující příkaz přidá Ironpythonu do seznamu:  
  
```  
[WebSiteProject("IronPython", "Iron Python")]public class PythonProjectPackage : ProjectPackage  
```  
  
 Tento atribut také nastaví cestu k šablonám tak, aby odkazovala na složku šablony. Další informace o umístění složky šablony najdete v tématu [šablony podpory](../../extensibility/internals/web-site-support-templates.md)webu.  
  
## <a name="websiteprojectrelatedfilesattribute"></a>WebSiteProjectRelatedFilesAttribute  
 Tento atribut je umístěn v projektu jazyka. Umožňuje projektu webu vnořit jeden typ souboru (související) do jiného typu souboru (primární) v **Průzkumník řešení**.  
  
 Příklad:  
  
```  
[WebSiteProjectRelatedFiles("aspx", "py")]public class PythonProjectPackage : ProjectPackage  
```  
  
 Určuje, že soubor codebehind Ironpythonu souvisí se souborem. aspx. Při vytvoření nové webové stránky. aspx v řešení webu Ironpythonu se vygeneruje nový zdrojový soubor. py, který se zobrazí jako podřízený uzel stránky ASPX.  
  
## <a name="provideintellisenseproviderattribute"></a>ProvideIntellisenseProviderAttribute  
 Tento atribut je umístěn v balíčku projektu jazyka. Vybírá poskytovatele technologie IntelliSense pro daný jazyk.  
  
 Příklad:  
  
```  
[ProvideIntellisenseProvider(typeof(PythonIntellisenseProvider), "IronPythonCodeProvider", "Iron Python", ".py", "IronPython;Python", "IronPython")]public class PythonPackage : Package, IOleComponent  
```  
  
 Určuje, že instance PythonIntellisenseProvider, která implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProject> , by měla být vytvořena na vyžádání pro poskytování jazykových služeb.  
  
 Implementace IVsIntellisenseProject zpracovává odkazy a volá kompilátor jazyka, když je vyžádána webová stránka s kódem, ale není uložena do mezipaměti.  
  
## <a name="see-also"></a>Viz také  
 [Podpora webu](../../extensibility/internals/web-site-support.md)
