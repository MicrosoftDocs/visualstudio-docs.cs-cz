---
title: Zabezpečení a lokalizovaná satelitní sestavení | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
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
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d817569a5f6709794b452fb5efe38d584669033f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49218644"
---
# <a name="security-and-localized-satellite-assemblies"></a>Zabezpečení a lokalizovaná satelitní sestavení
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pokud hlavní sestavení používá silné názvy, musí být stejný soukromý klíč jako hlavní sestavení podepsáno satelitních sestavení. Pokud zadaný klíč veřejného/soukromého pár mezi hlavní a satelitní sestavení, vaše prostředky se neshoduje se nenačte. Další informace o podepisování sestavení naleznete v tématu [postupy: podepsání sestavení silným názvem](http://msdn.microsoft.com/library/2c30799a-a826-46b4-a25d-c584027a6c67).  
  
 Obecně platí budete muset mít podpisový skupin vaší organizace nebo externí podpisový organizace přihlásit s privátním klíčem. Je to z důvodu citlivosti privátního klíče: přístup je často omezené na několika jednotlivcům. Můžete použít zpožděného podepisování během vývoje. Další informace najdete v tématu [zpožděné podepisování sestavení](http://msdn.microsoft.com/library/9d300e17-5bf1-4360-97da-2aa55efd9070).  
  
## <a name="see-also"></a>Viz také  
 [Důležité informace o zabezpečení sestavení](http://msdn.microsoft.com/library/1b5439c1-f3d5-4529-bd69-01814703d067)   
 [Klíčové koncepty zabezpečení](http://msdn.microsoft.com/library/3cfced4f-ea02-4e66-ae98-d69286363e98)   
 [Představení mezinárodních aplikací založených na rozhraní .NET Framework](../ide/introduction-to-international-applications-based-on-the-dotnet-framework.md)   
 [Lokalizace aplikací](../ide/localizing-applications.md)   
 [Globalizace a lokalizace aplikací](../ide/globalizing-and-localizing-applications.md)

