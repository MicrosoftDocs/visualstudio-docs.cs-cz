---
title: Implementace jedním souborem generátory | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- custom tools, implementing
- projects [Visual Studio SDK], extensibility
- projects [Visual Studio SDK], managed custom tools
ms.assetid: fe9ef6b6-4690-4c2c-872c-301c980d17fe
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 71db8036634cfc266db3c585c48317262f48b367
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31129360"
---
# <a name="implementing-single-file-generators"></a>Implementace generátory jedním souborem
Vlastní nástroj – někdy označovány jako generátor jednoho souboru – umožňuje rozšířit [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] a [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] projektu systémy v [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Vlastní nástroj je komponenty modelu COM, který implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> rozhraní. Použití tohoto rozhraní, transformuje vlastní nástroj jeden vstupní soubor do jednoho výstupního souboru. Výsledek transformace může být zdrojový kód nebo jakékoliv výstup, který je užitečné. Dva příklady vlastní nástroj generuje kód souborů jsou kódu vygenerované v reakci na změny v souborech generována pomocí webové služby popis Language (WSDL) a vizuálního návrháře.  
  
 Pokud vlastní nástroj je načtena, nebo vstupní soubor zůstane uložen, systém projektu volá <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> metoda a obsahuje odkaz na <xref:Microsoft.VisualStudio.Shell.Interop.IVsGeneratorProgress> rozhraní zpětného volání, které nástroj mohou zasílat zprávy o jejím průběhu uživateli.  
  
 Výstupního souboru, který vlastní nástroj generuje se přidá do projektu se závislostí na vstupní soubor. Systém projektu automaticky určuje název výstupního souboru, založené na řetězci vrácený implementace vlastního nástroje <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>.  
  
 Musí implementovat vlastní nástroj <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> rozhraní. Volitelně vlastních nástrojů podpory <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite> rozhraní k načtení informací z jiných zdrojů než vstupní soubor. V každém případě před vlastní nástroj můžete použít, je nutné zaregistrovat ji pomocí systému nebo v [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] místním registru. Další informace o registraci vlastních nástrojů najdete v tématu [registrace generátory jeden soubor](../../extensibility/internals/registering-single-file-generators.md).  
  
## <a name="see-also"></a>Viz také  
 [Zveřejnění typů pro vizuální návrháře](../../extensibility/internals/exposing-types-to-visual-designers.md)