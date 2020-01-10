---
title: Podpora automatizace pro stránky možností | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], automation support
- automation [Visual Studio SDK], creating Tools Options pages
ms.assetid: 0b25b82c-7432-4e0a-9e84-350269ba8260
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 03360bfc01110e7b4ef73956f0199aaaed9cee2c
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/10/2020
ms.locfileid: "75848971"
---
# <a name="automation-support-for-options-pages"></a>Podpora automatizace pro stránky možností
Sady VSPackage mohou poskytnout dialogová okna vlastních **možností** do nabídky **nástroje** (stránky**možností nástrojů** ) v [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] a mohou je zpřístupnit modelu automatizace.

## <a name="tools-options-pages"></a>stránky Možnosti nástrojů
 Aby bylo možné vytvořit stránku **možností nástroje** , VSPackage musí poskytnout implementaci uživatelského ovládacího prvku vrácenou do prostředí prostřednictvím implementace <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> metody VSPackage. (Nebo, pro spravovaný kód, metoda <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>.)

 Je volitelná, ale důrazně se doporučuje, aby byl přístup k této nové stránce povolen pomocí modelu automatizace. Můžete to udělat pomocí následujících kroků:

1. Rozšíří objekt <xref:EnvDTE._DTE.Properties%2A> pomocí implementace objektu odvozeného rozhraním IDispatch.

2. Vraťte implementaci metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> (nebo pro spravovaný kód metodu <xref:Microsoft.VisualStudio.Shell.Package.GetAutomationObject%2A>) na objekt odvozený od rozhraní IDispatch.

3. Když příjemce automatizace volá metodu <xref:EnvDTE._DTE.Properties%2A> na stránce vlastností vlastní **Možnosti** , prostředí používá metodu <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> k získání vlastní implementace automatizace stránky **možností nástrojů** .

4. Automatizační objekt sady VSPackage se pak použije k poskytnutí každého <xref:EnvDTE.Property> vráceného <xref:EnvDTE._DTE.Properties%2A>.

   Ukázku implementace vlastní **Možnosti nástrojů** naleznete v tématu [VSSDK Samples](https://github.com/Microsoft/VSSDK-Extensibility-Samples).

## <a name="see-also"></a>Viz také:
- [Vystavení objektů projektu](../../extensibility/internals/exposing-project-objects.md)
