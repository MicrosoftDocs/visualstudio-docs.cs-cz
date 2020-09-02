---
title: Zjednodušené vkládání | Microsoft Docs
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
ms.openlocfilehash: b9bc9619ae1ed75aed3656ff014296f7c7d88fa0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80700077"
---
# <a name="simplified-embedding"></a>Zjednodušená vkládání
Zjednodušené vkládání je povoleno v editoru, když je jeho objekt zobrazení dokumentu nadřazený (tj. vytvořený podřízený objekt) [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] a <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> rozhraní je implementováno pro zpracování příkazů okna. Zjednodušené editory vkládání nemohou hostovat aktivní ovládací prvky. Na následujícím obrázku jsou uvedeny objekty, které slouží k vytvoření editoru s zjednodušeným vkládáním.

 ![Obrázek zjednodušeného editoru vkládání](../extensibility/media/vssimplifiedembeddingeditor.gif "vsSimplifiedEmbeddingEditor") Editor s zjednodušeným vkládáním

> [!NOTE]
> Z objektů na tomto obrázku `CYourEditorFactory` je vyžadován pouze objekt pro vytvoření standardního editoru založeného na souborech. Pokud vytváříte vlastní editor, nemusíte implementovat <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> , protože editor pravděpodobně bude mít vlastní privátní mechanismus trvalosti. Pro nevlastní editory je však třeba provést.

 Všechna rozhraní implementovaná pro vytvoření editoru s zjednodušeným vkládáním jsou obsažena v `CYourEditorDocument` objektu. Chcete-li však podporovat více zobrazení dat dokumentu, rozdělte rozhraní na samostatná data a zobrazte objekty, jak je uvedeno v následující tabulce.

|Rozhraní|Umístění rozhraní|Použití|
|---------------|---------------------------|---------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Zobrazení|Poskytuje připojení k nadřazenému oknu.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Zobrazení|Zpracovává příkazy.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>|Zobrazení|Povolí aktualizace stavového řádku.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser>|Zobrazení|Povolí položky **panelu nástrojů** .|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEvents>|Data|Odesílá oznámení při změně souboru.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|Data|Povolí funkci Uložit jako pro typ souboru.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>|Data|Povoluje stálost dokumentu.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl>|Data|Umožňuje potlačit události změny souborů, jako je například opakované spuštění.|
