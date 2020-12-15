---
title: Atributy podpory webu | Microsoft Docs
description: Přečtěte si o atributech podpory webu, které jsou nezbytné pro rozšíření funkcí sady Visual Studio pomocí projektů webu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- web site projects, registration
ms.assetid: 46d52e2c-ca2a-4bbd-8500-5b0129768aec
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9beee39ca6968b0922bc134fa21e0cde3d6dd3b6
ms.sourcegitcommit: 19061b61759ce8e3b083a0e01a858e5435580b3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/15/2020
ms.locfileid: "97487865"
---
# <a name="web-site-support-attributes"></a>Atributy podpory webu
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Webový projekt lze rozšířit tak, aby poskytoval podporu webových programovacích jazyků. Jazyk se musí zaregistrovat [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , aby se šablony projektu mohly zobrazit v dialogovém okně **Nový web** , když je vybraný jazyk.

Ukázka Ironpythonu studia zahrnuje podporu webu. Ukázka obsahuje následující třídy atributů k registraci Ironpythonu jako jazyk CodeBehind pro nové webové projekty.

## <a name="websiteprojectattribute"></a>WebSiteProjectAttribute
 Tento atribut je umístěn v projektu jazyka. Přidá jazyk do seznamu jazyků webového programování v seznamu **jazyk** v dialogovém okně **Nový web** . Například následující kód přidá do seznamu Ironpythonu:

```
[WebSiteProject("IronPython", "Iron Python")]
public class PythonProjectPackage : ProjectPackage
```

 Tento atribut také nastaví cestu k šablonám tak, aby odkazovala na složku šablony. Další informace o umístění složky šablony najdete v tématu [šablony podpory](../../extensibility/internals/web-site-support-templates.md)webu.

## <a name="websiteprojectrelatedfilesattribute"></a>WebSiteProjectRelatedFilesAttribute
 Tento atribut je umístěn v projektu jazyka. Umožňuje projektu webu vnořit jeden typ souboru (související) do jiného typu souboru (primární) v **Průzkumník řešení**.

 Například následující kód určuje, že soubor codebehind Ironpythonu souvisí se souborem. aspx. Při vytvoření nové webové stránky. aspx v řešení webu Ironpythonu se vygeneruje nový zdrojový soubor. py, který se zobrazí jako podřízený uzel stránky ASPX.

```
[WebSiteProjectRelatedFiles("aspx", "py")]
public class PythonProjectPackage : ProjectPackage
```

## <a name="provideintellisenseproviderattribute"></a>ProvideIntellisenseProviderAttribute
 Tento atribut je umístěn v balíčku projektu jazyka. Vybírá poskytovatele technologie IntelliSense pro daný jazyk.

 Například následující kód určuje, že instance PythonIntellisenseProvider, která implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProject> , by měla být vytvořena na vyžádání pro poskytování jazykových služeb.

```
[ProvideIntellisenseProvider(typeof(PythonIntellisenseProvider), "IronPythonCodeProvider", "Iron Python", ".py", "IronPython;Python", "IronPython")]
public class PythonPackage : Package, IOleComponent
```

 Implementace IVsIntellisenseProject zpracovává odkazy a volá kompilátor jazyka, když je vyžádána webová stránka s kódem, ale není uložena do mezipaměti.

## <a name="see-also"></a>Viz také
- [Podpora webu](../../extensibility/internals/web-site-support.md)
