---
title: 'Postupy: určení umístění, kde budou koncoví uživatelé instalovat z | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [ClickOnce], specifying an installation URL
- URLs, specifying an installation URL
- installation, specifying installation an URL
- Installation URL property
ms.assetid: 04a804bf-ed55-4a7a-a1e6-f63ed99c0276
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6b0731a5e218b6fcd6a13ac00fe19daad86f6b3d
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/17/2018
ms.locfileid: "39078082"
---
# <a name="how-to-specify-the-location-where-end-users-will-install-from"></a>Postupy: určení umístění, kde budou koncoví uživatelé instalovat z
Při publikování [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace, umístění, kde uživatelé ke stažení a instalaci aplikace není nutně umístění, kde nejprve publikovat aplikace. Například v některých organizacích může vývojář publikování aplikace na testovacím serveru a pak by správce přesunout aplikaci na webový server.  
  
 V takovém případě můžete použít `Installation URL` vlastnosti a určit tak webový server, kde budou moct uživatelé aplikaci stáhnout. To je nezbytné, aby manifest aplikace věděla, kam chcete vyhledat aktualizace.  
  
 `Installation URL` Vlastnost lze nastavit na **publikovat** stránku **Návrháře projektu**.  
  
 **Poznámka:** `Installation URL` vlastnost můžete nastavit také pomocí **PublishWizard**. Další informace najdete v tématu [postupy: publikování aplikace ClickOnce pomocí Průvodce publikováním](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
### <a name="to-specify-an-installation-url"></a>Chcete zadat adresu URL instalace  
  
1.  S projekt vybraný v **Průzkumníka řešení**na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.  
  
2.  Klikněte na tlačítko **publikovat** kartu.  
  
3.  Do pole Adresa URL instalace, zadejte umístění instalace pomocí plně kvalifikovanou adresu URL pomocí formátu *http://www.microsoft.com/ApplicationName*, nebo cestu UNC ve formátu  *\\\Server\ApplicationName*.  
  
## <a name="see-also"></a>Viz také:  
 [Postupy: určení, kde sada Visual Studio zkopíruje soubory](../deployment/how-to-specify-where-visual-studio-copies-the-files.md)   
 [Publikování aplikací ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Postupy: publikování aplikace ClickOnce pomocí Průvodce publikováním](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)