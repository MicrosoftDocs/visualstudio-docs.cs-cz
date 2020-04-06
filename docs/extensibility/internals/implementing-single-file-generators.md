---
title: Implementace jednosouborových generátorů | Dokumenty společnosti Microsoft
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
ms.openlocfilehash: e700d09277edbb04b30676d3965b6c996d0a11f3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707660"
---
# <a name="implementing-single-file-generators"></a>Implementace generátorů tvořených jedním souborem
Vlastní nástroj – někdy označovaný jako generátor jednoho souboru [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] – lze [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]použít k rozšíření a projektových systémů v aplikaci . Vlastní nástroj je komponenta modelu <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> COM, která implementuje rozhraní. Pomocí tohoto rozhraní vlastní nástroj transformuje jeden vstupní soubor do jednoho výstupního souboru. Výsledkem transformace může být zdrojový kód nebo jakýkoli jiný výstup, který je užitečný. Dva příklady vlastních souborů kódu generovaných nástroji jsou kód generovaný v reakci na změny ve vizuálním návrháři a soubory generované pomocí jazyka WSDL (Web Services Description Language).

 Při načtení vlastního nástroje nebo uložení vstupního souboru <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> systém projektu volá metodu <xref:Microsoft.VisualStudio.Shell.Interop.IVsGeneratorProgress> a předá odkaz na rozhraní zpětného volání, čímž může nástroj hlásit svůj průběh uživateli.

 Výstupní soubor, který generuje vlastní nástroj je přidán do projektu se závislostí na vstupní soubor. Systém projektu automaticky určí název výstupního souboru na základě řetězce vráceného implementací vlastního nástroje . <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>

 Vlastní nástroj musí <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> implementovat rozhraní. Volitelně vlastní nástroje <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite> podporují rozhraní pro načtení informací z jiných zdrojů než vstupnísoubor. V každém případě, než budete moci použít vlastní nástroj, musíte [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] jej zaregistrovat v systému nebo v místním registru. Další informace o registraci vlastních nástrojů naleznete v [tématu Registrace generátorů jednotlivých souborů](../../extensibility/internals/registering-single-file-generators.md).

## <a name="see-also"></a>Viz také
- [Zveřejnění typů pro vizuální návrháře](../../extensibility/internals/exposing-types-to-visual-designers.md)
