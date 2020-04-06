---
title: Podpora automatizace pro stránky možností | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], automation support
- automation [Visual Studio SDK], creating Tools Options pages
ms.assetid: 0b25b82c-7432-4e0a-9e84-350269ba8260
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fe45238948d5b4cdebbf9f002f6b242515e7622e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709934"
---
# <a name="automation-support-for-options-pages"></a>Podpora automatizace pro stránky Možnosti
VSPackages můžete poskytnout vlastní **možnosti** dialogových oken do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nabídky **Nástroje** **(Nástroje Možnosti** stránky) v a může zpřístupnit je pro model automatizace.

## <a name="tools-options-pages"></a>stránky Možnosti nástrojů
 Chcete-li vytvořit tools **options** stránku, VSPackage musí poskytnout implementaci uživatelského ovládacího prvku <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> vrácena do prostředí prostřednictvím implementace VSPackage metody. (Nebo pro spravovaný <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> kód metoda.)

 Je volitelné, ale důrazně doporučujeme, aby přístup k této nové stránce prostřednictvím modelu automatizace. Můžete tak učinit pomocí následujících kroků:

1. Rozšiřte <xref:EnvDTE._DTE.Properties%2A> objekt prostřednictvím implementace objektu odvozeného z IDispatch.

2. Vrátí implementaci <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> metody (nebo pro spravovaný kód <xref:Microsoft.VisualStudio.Shell.Package.GetAutomationObject%2A> metody) na objekt odvozený od IDispatch.

3. Když spotřebitel automatizace <xref:EnvDTE._DTE.Properties%2A> volá metodu na **vlastní** option <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> vlastnost stránky, prostředí používá metodu k získání vlastní **tools možnosti** implementace automatizace stránky.

4. Objekt automatizace VSPackage se pak používá <xref:EnvDTE.Property> k <xref:EnvDTE._DTE.Properties%2A>poskytnutí každé vrácené .

   Ukázka implementace vlastní stránky **Možnosti nástrojů** naleznete [v tématu Ukázky sady VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples).

## <a name="see-also"></a>Viz také
- [Vystavit objekty projektu](../../extensibility/internals/exposing-project-objects.md)
