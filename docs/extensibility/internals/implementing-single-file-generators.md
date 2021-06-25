---
title: Implementace Single-File generátorů | Microsoft Docs
description: Naučte se používat vlastní nástroj, který implementuje rozhraní IVsSingleFileGenerator k rozšíření systémů projektů Visual Basic a Visual C# v Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- custom tools, implementing
- projects [Visual Studio SDK], extensibility
- projects [Visual Studio SDK], managed custom tools
ms.assetid: fe9ef6b6-4690-4c2c-872c-301c980d17fe
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 11ce8a69841d18d383e9d8e12c14d7af652d9cb8
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900028"
---
# <a name="implementing-single-file-generators"></a>Implementace generátorů tvořených jedním souborem
K rozšíření systémů projektů a v nástroji lze použít vlastní nástroj , někdy označový jako generátor [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] jediného [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] souboru. Vlastní nástroj je komponenta modelu COM, která implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> rozhraní. Pomocí tohoto rozhraní vlastní nástroj transformuje jeden vstupní soubor do jednoho výstupního souboru. Výsledkem transformace může být zdrojový kód nebo jakýkoli jiný výstup, který je užitečný. Dvěma příklady vlastních souborů kódu generovaných nástrojem je kód vygenerovaný v reakci na změny ve vizuálním návrháři a soubory generované pomocí jazyka WSDL (Web Services Description Language).

 Při načtení vlastního nástroje nebo uložení vstupního souboru volá systém projektu metodu a předá odkaz do rozhraní zpětného volání, kde nástroj může uživateli nahlásit <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsGeneratorProgress> průběh.

 Výstupní soubor, který vlastní nástroj vygeneruje, se přidá do projektu se závislostí na vstupním souboru. Systém projektu automaticky určí název výstupního souboru na základě řetězce vráceného implementací vlastního nástroje <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A> .

 Vlastní nástroj musí implementovat <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> rozhraní . Volitelně vlastní nástroje podporují rozhraní <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite> pro načtení informací z jiných zdrojů než ze vstupního souboru. Před použitím vlastního nástroje ho musíte v každém případě zaregistrovat v systému nebo v [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] místním registru. Další informace o registraci vlastních nástrojů najdete v tématu [Registrace generátorů jednoduchých souborů.](../../extensibility/internals/registering-single-file-generators.md)

## <a name="see-also"></a>Viz také
- [Zveřejnění typů pro vizuální návrháře](../../extensibility/internals/exposing-types-to-visual-designers.md)
