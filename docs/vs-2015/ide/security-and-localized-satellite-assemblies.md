---
title: Zabezpečení a lokalizovaná satelitní sestavení | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- key pairs for strong-named assemblies
- strong-named assemblies, security considerations
- satellite assemblies, localized
- code signing, assemblies
- security [Visual Studio], assemblies
- strong-named assemblies, localized
- assemblies [Visual Studio], security
- localization, satellite assemblies
ms.assetid: 6d953840-b301-47d5-8d34-30c1b29b5071
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 866e313a36af5ef72f910a5eafbf7b31c971d890
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672909"
---
# <a name="security-and-localized-satellite-assemblies"></a>Zabezpečení a lokalizovaná satelitní sestavení
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pokud vaše hlavní sestavení používá silné pojmenování, satelitní sestavení musí být podepsáno stejným privátním klíčem jako hlavní sestavení. Pokud pár veřejného a privátního klíče se neshoduje mezi hlavními a satelitními sestaveními, prostředky nebudou načteny. Další informace o podpisových sestaveních naleznete v tématu [How to: Sign a Assembly se silným názvem](https://msdn.microsoft.com/library/2c30799a-a826-46b4-a25d-c584027a6c67).

 Obecně platí, že musíte mít podpisovou skupinu vaší organizace nebo externí podpisovou organizaci s privátním klíčem. Důvodem je citlivá povaha privátního klíče: přístup je často omezen na několik jednotlivců. Během vývoje můžete použít zpožděné podepisování. Další informace naleznete v tématu [Zpožděné podepisování sestavení](https://msdn.microsoft.com/library/9d300e17-5bf1-4360-97da-2aa55efd9070).

## <a name="see-also"></a>Viz také
 [Důležité informace o zabezpečení sestavení –](https://msdn.microsoft.com/library/1b5439c1-f3d5-4529-bd69-01814703d067) [klíčové pojmy zabezpečení](https://msdn.microsoft.com/library/3cfced4f-ea02-4e66-ae98-d69286363e98) [Úvod k mezinárodním aplikacím na základě .NET Framework](../ide/introduction-to-international-applications-based-on-the-dotnet-framework.md) [lokalizace aplikací](../ide/localizing-applications.md) [a lokalizace aplikací](../ide/globalizing-and-localizing-applications.md)
