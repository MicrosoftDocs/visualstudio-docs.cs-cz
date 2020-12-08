---
title: Implementace generátorů Single-File | Microsoft Docs
description: Naučte se používat vlastní nástroj, který implementuje rozhraní IVsSingleFileGenerator pro rozšiřování Visual Basic a systémů projektů Visual C# v aplikaci Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- custom tools, implementing
- projects [Visual Studio SDK], extensibility
- projects [Visual Studio SDK], managed custom tools
ms.assetid: fe9ef6b6-4690-4c2c-872c-301c980d17fe
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 373536844e3572e2e61b56c1b86f3e00ed47845d
ms.sourcegitcommit: 2f964946d7044cc7d49b3fc10b413ca06cb2d11b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2020
ms.locfileid: "96761241"
---
# <a name="implementing-single-file-generators"></a>Implementace generátorů tvořených jedním souborem
Vlastní nástroj (někdy označovaný jako generátor jediného souboru) lze použít k rozšiřování [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] systémů a systémů projektů v nástroji [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Vlastní nástroj je komponenta modelu COM, která implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> rozhraní. Pomocí tohoto rozhraní vlastní nástroj transformuje jeden vstupní soubor do jednoho výstupního souboru. Výsledkem transformace může být zdrojový kód nebo jakýkoli jiný výstup, který je užitečný. Dva příklady souborů kódu generovaných vlastním nástrojem jsou generovány v reakci na změny ve vizuálním návrháři a v souborech vygenerovaných pomocí jazyka WSDL (Web Services Description Language).

 Když je načten vlastní nástroj nebo je uložen vstupní soubor, systém projektu zavolá <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> metodu a předá odkaz na <xref:Microsoft.VisualStudio.Shell.Interop.IVsGeneratorProgress> rozhraní zpětného volání, které může nástroj nahlásit svůj průběh uživateli.

 Výstupní soubor, který vlastní nástroj generuje, je přidán do projektu se závislostí na vstupním souboru. Systém projektu automaticky určí název výstupního souboru na základě řetězce vráceného implementací vlastního nástroje <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A> .

 Vlastní nástroj musí implementovat <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> rozhraní. Volitelně vlastní nástroje podporují <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite> rozhraní k načítání informací z jiných zdrojů než vstupního souboru. V každém případě je třeba před použitím vlastního nástroje ho zaregistrovat v systému nebo v [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] místním registru. Další informace o registraci vlastních nástrojů naleznete v tématu [Registering Single File generátors](../../extensibility/internals/registering-single-file-generators.md).

## <a name="see-also"></a>Viz také
- [Zveřejnění typů pro vizuální návrháře](../../extensibility/internals/exposing-types-to-visual-designers.md)
