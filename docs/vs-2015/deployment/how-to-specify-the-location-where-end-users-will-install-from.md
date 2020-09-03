---
title: 'Postupy: určení umístění, ze kterého budou koncoví uživatelé instalovat | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 82181d906adc3454dfe77ef4fb21d8bdf99df16f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "77557983"
---
# <a name="how-to-specify-the-location-where-end-users-will-install-from"></a>Postupy: Určení umístění, z něhož mohou instalovat koncoví uživatelé
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Při publikování [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace není umístění, kde uživatelé najdou ke stažení a instalaci aplikace, nutně umístění, kam aplikaci poprvé publikujete. V některých organizacích může vývojář například publikovat aplikaci na přípravném serveru a potom Správce přesune aplikaci na webový server.  
  
 V takovém případě můžete použít `Installation URL` vlastnost k určení webového serveru, kde budou uživatelé stahovat aplikaci. To je nezbytné, aby manifest aplikace věděl, kde hledat aktualizace.  
  
 `Installation URL`Vlastnost lze nastavit na stránce **publikovat** v **Návrháři projektu**.  
  
 **Poznámka:** `Installation URL` Vlastnost lze také nastavit pomocí **PublishWizard**. Další informace naleznete v tématu [How to: Publish a aplikace ClickOnce using the Publish Wizard](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
### <a name="to-specify-an-installation-url"></a>Určení instalační adresy URL  
  
1. S projektem vybraným v **Průzkumník řešení**v nabídce **projekt** klikněte na **vlastnosti**.  
  
2. Klikněte na kartu **publikovat** .  
  
3. V poli Adresa URL instalace zadejte umístění instalace pomocí plně kvalifikované adresy URL ve formátu `https://www.contoso.com/ApplicationName` nebo cesty UNC ve formátu `\\Server\ApplicationName` .  
  
## <a name="see-also"></a>Viz také  
 [Postupy: určení umístění, kam aplikace Visual Studio kopíruje soubory](../deployment/how-to-specify-where-visual-studio-copies-the-files.md)   
 [Publikování aplikací ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Postupy: Publikování aplikace ClickOnce pomocí průvodce publikováním](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
