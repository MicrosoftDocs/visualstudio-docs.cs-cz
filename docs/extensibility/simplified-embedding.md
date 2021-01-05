---
title: Zjednodušené vkládání | Microsoft Docs
description: Přečtěte si o zjednodušeném vkládání, které lze povolit v editoru, pokud je jeho objekt zobrazení dokumentu podřízeným prvkem sady Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - simple view embedding
ms.assetid: f1292478-a57d-48ec-8c9e-88a23f04ffe5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 99aaf5070646bbbb95c6be98eb8ac2f7a5948ff2
ms.sourcegitcommit: 94a57a7bda3601b83949e710a5ca779c709a6a4e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2020
ms.locfileid: "97715272"
---
# <a name="simplified-embedding"></a>Zjednodušená vkládání
Zjednodušené vkládání je povoleno v editoru, když je jeho objekt zobrazení dokumentu nadřazený (tj. vytvořený podřízený objekt) [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] a <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> rozhraní je implementováno pro zpracování příkazů okna. Zjednodušené editory vkládání nemohou hostovat aktivní ovládací prvky. Na následujícím obrázku jsou uvedeny objekty, které slouží k vytvoření editoru s zjednodušeným vkládáním.

 ![Obrázek zjednodušeného editoru vkládání](../extensibility/media/vssimplifiedembeddingeditor.gif "vsSimplifiedEmbeddingEditor") Editor s zjednodušeným vkládáním

> [!NOTE]
> Z objektů na tomto obrázku `CYourEditorFactory` je vyžadován pouze objekt pro vytvoření standardního editoru založeného na souborech. Pokud vytváříte vlastní editor, nemusíte implementovat <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> , protože editor pravděpodobně bude mít vlastní privátní mechanismus trvalosti. Pro nevlastní editory je však třeba provést.

 Všechna rozhraní implementovaná pro vytvoření editoru s zjednodušeným vkládáním jsou obsažena v `CYourEditorDocument` objektu. Chcete-li však podporovat více zobrazení dat dokumentu, rozdělte rozhraní na samostatná data a zobrazte objekty, jak je uvedeno v následující tabulce.

|Rozhraní|Umístění rozhraní|Použití|
|---------------|---------------------------|---------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Zobrazit|Poskytuje připojení k nadřazenému oknu.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Zobrazit|Zpracovává příkazy.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>|Zobrazit|Povolí aktualizace stavového řádku.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser>|Zobrazit|Povolí položky **panelu nástrojů** .|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEvents>|Data|Odesílá oznámení při změně souboru.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|Data|Povolí funkci Uložit jako pro typ souboru.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>|Data|Povoluje stálost dokumentu.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl>|Data|Umožňuje potlačit události změny souborů, jako je například opakované spuštění.|
