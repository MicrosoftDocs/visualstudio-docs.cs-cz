---
title: Implementace generátorů tvořených jedním souborem | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- custom tools, implementing
- projects [Visual Studio SDK], extensibility
- projects [Visual Studio SDK], managed custom tools
ms.assetid: fe9ef6b6-4690-4c2c-872c-301c980d17fe
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 69bde665e62d063b6bab8784634777eeea02e941
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72727181"
---
# <a name="implementing-single-file-generators"></a>Implementace generátorů tvořených jedním souborem
Vlastní nástroj, který se někdy označuje jako generátor tvořený jedním souborem, se dá použít k rozšiřování [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] a [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] systémů projektů v [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Vlastní nástroj je komponenta modelu COM, která implementuje rozhraní <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>. Pomocí tohoto rozhraní vlastní nástroj transformuje jeden vstupní soubor do jednoho výstupního souboru. Výsledkem transformace může být zdrojový kód nebo jakýkoli jiný výstup, který je užitečný. Dva příklady souborů kódu generovaných vlastním nástrojem jsou generovány v reakci na změny ve vizuálním návrháři a v souborech vygenerovaných pomocí jazyka WSDL (Web Services Description Language).

 Když je načten vlastní nástroj nebo je uložen vstupní soubor, systém projektu zavolá metodu <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> a předá odkaz na rozhraní <xref:Microsoft.VisualStudio.Shell.Interop.IVsGeneratorProgress> zpětného volání, které může nástroj nahlásit svůj průběh uživateli.

 Výstupní soubor, který vlastní nástroj generuje, je přidán do projektu se závislostí na vstupním souboru. Systém projektu automaticky určí název výstupního souboru na základě řetězce vráceného implementací <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A> vlastního nástroje.

 Vlastní nástroj musí implementovat rozhraní <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>. Volitelně vlastní nástroje podporují rozhraní <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite>, aby načetla informace z jiných zdrojů, než je vstupní soubor. V každém případě je třeba před použitím vlastního nástroje jej zaregistrovat v systému nebo v [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] místním registru. Další informace o registraci vlastních nástrojů naleznete v tématu [Registering Single File generátors](../../extensibility/internals/registering-single-file-generators.md).

## <a name="see-also"></a>Viz také:
- [Zveřejnění typů pro vizuální návrháře](../../extensibility/internals/exposing-types-to-visual-designers.md)