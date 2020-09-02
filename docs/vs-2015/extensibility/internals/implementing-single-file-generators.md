---
title: Implementace generátorů tvořených jedním souborem | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- custom tools, implementing
- projects [Visual Studio SDK], extensibility
- projects [Visual Studio SDK], managed custom tools
ms.assetid: fe9ef6b6-4690-4c2c-872c-301c980d17fe
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e2ca842f05692d5d47ed42470f58f2be0bb45007
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68192700"
---
# <a name="implementing-single-file-generators"></a>Implementace generátorů tvořených jedním souborem
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vlastní nástroj (někdy označovaný jako generátor jediného souboru) lze použít k rozšiřování [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] [!INCLUDE[csprcs](../../includes/csprcs-md.md)] systémů a systémů projektů v nástroji [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Vlastní nástroj je komponenta modelu COM, která implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> rozhraní. Pomocí tohoto rozhraní vlastní nástroj transformuje jeden vstupní soubor do jednoho výstupního souboru. Výsledkem transformace může být zdrojový kód nebo jakýkoli jiný výstup, který je užitečný. Dva příklady souborů kódu generovaných vlastním nástrojem jsou generovány v reakci na změny ve vizuálním návrháři a v souborech vygenerovaných pomocí jazyka WSDL (Web Services Description Language).  
  
 Když je načten vlastní nástroj nebo je uložen vstupní soubor, systém projektu zavolá <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> metodu a předá odkaz na <xref:Microsoft.VisualStudio.Shell.Interop.IVsGeneratorProgress> rozhraní zpětného volání, které může nástroj nahlásit svůj průběh uživateli.  
  
 Výstupní soubor, který vlastní nástroj generuje, je přidán do projektu se závislostí na vstupním souboru. Systém projektu automaticky určí název výstupního souboru na základě řetězce vráceného implementací vlastního nástroje <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A> .  
  
 Vlastní nástroj musí implementovat <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> rozhraní. Volitelně vlastní nástroje podporují <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite> rozhraní k načítání informací z jiných zdrojů než vstupního souboru. V každém případě je třeba před použitím vlastního nástroje ho zaregistrovat v systému nebo v [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] místním registru. Další informace o registraci vlastních nástrojů naleznete v tématu [Registering Single File generátors](../../extensibility/internals/registering-single-file-generators.md).  
  
## <a name="see-also"></a>Viz také  
 [Určení výchozího oboru názvů projektu](../../misc/determining-the-default-namespace-of-a-project.md)   
 [Zveřejnění typů pro vizuální návrháře](../../extensibility/internals/exposing-types-to-visual-designers.md)
