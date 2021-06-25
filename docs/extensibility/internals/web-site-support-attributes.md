---
title: Atributy podpory webu | Microsoft Docs
description: Seznamte se s atributy podpory webu, které jsou nezbytné k rozšíření funkčnosti Visual Studio pomocí webových projektů.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- web site projects, registration
ms.assetid: 46d52e2c-ca2a-4bbd-8500-5b0129768aec
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 348fd16234e38cd7832ae18e7b28e6abe0bc63d9
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901770"
---
# <a name="web-site-support-attributes"></a>Atributy podpory webu
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Projekt webu lze rozšířit o podporu programovacích jazyků webu. Jazyk se musí zaregistrovat pomocí , aby se šablony projektů po výběru jazyka v dialogovém okně Nový web [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] objevily. 

Ukázka IronPython Studia zahrnuje podporu webu. Ukázka obsahuje následující třídy atributů pro registraci IronPythonu jako jazyka s kódem pro nové webové projekty.

## <a name="websiteprojectattribute"></a>Atribut WebSiteProjectAttribute
 Tento atribut je umístěn v projektu jazyka. Tento jazyk se přidá do seznamu programovacích jazyků webu v **seznamu** Jazyk v **dialogovém okně Nový** web. Například následující kód přidá IronPython do seznamu:

```
[WebSiteProject("IronPython", "Iron Python")]
public class PythonProjectPackage : ProjectPackage
```

 Tento atribut také nastaví cestu k šablonám tak, aby odkazovat na složku templates. Další informace o umístění složky templates najdete v tématu [Šablony podpory webu](../../extensibility/internals/web-site-support-templates.md).

## <a name="websiteprojectrelatedfilesattribute"></a>Atribut WebSiteProjectRelatedFilesAttribute
 Tento atribut je umístěn v projektu jazyka. Umožňuje projektu webu vnořit jeden typ souboru (související) do jiného typu souboru (primární) v **Průzkumník řešení**.

 Například následující kód určuje, že soubor IronPython codebehind souvisí se souborem .aspx. Když se v řešení webu IronPython vytvoří nová webová stránka .aspx, vygeneruje se nový zdrojový soubor .py, který se zobrazí jako podřízený uzel stránky .aspx.

```
[WebSiteProjectRelatedFiles("aspx", "py")]
public class PythonProjectPackage : ProjectPackage
```

## <a name="provideintellisenseproviderattribute"></a>ProvideIntellisenseProviderAttribute
 Tento atribut je umístěn na balíček projektu jazyka. Vybere zprostředkovatele IntelliSense pro jazyk.

 Například následující kód určuje, že instance PythonIntellisenseProvider, která implementuje , by měla být vytvořena na vyžádání za účelem <xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProject> poskytování jazykových služeb.

```
[ProvideIntellisenseProvider(typeof(PythonIntellisenseProvider), "IronPythonCodeProvider", "Iron Python", ".py", "IronPython;Python", "IronPython")]
public class PythonPackage : Package, IOleComponent
```

 Implementace IVsIntellisenseProject zpracovává odkazy a volá kompilátor jazyka, když se požaduje webová stránka s kódem, ale není uložená v mezipaměti.

## <a name="see-also"></a>Viz také
- [Podpora webu](../../extensibility/internals/web-site-support.md)
