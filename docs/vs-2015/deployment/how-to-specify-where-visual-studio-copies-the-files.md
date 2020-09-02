---
title: 'Postupy: určení umístění, kde aplikace Visual Studio 2015 kopíruje soubory | Microsoft Docs'
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- publishing, specifying location
- Publish Location property
ms.assetid: 6c552700-dda3-49fe-af98-4717344fda07
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8759145dd4a7647cad6e9964ae1f1c97d333b626
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65226158"
---
# <a name="how-to-specify-where-visual-studio-copies-the-files"></a>Postupy: Určení cíle kopírování souborů sadou Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Při publikování aplikace pomocí ClickOnce `Publish Location` vlastnost určuje umístění, kam jsou umístěny soubory aplikace a manifest. Může to být cesta k souboru nebo cesta k serveru FTP.

 Vlastnost můžete zadat `Publish Location` na stránce **publikovat** v **Návrháři projektu**nebo pomocí Průvodce publikováním. Další informace naleznete v tématu [How to: Publish a aplikace ClickOnce using the Publish Wizard](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).

> [!NOTE]
> Při instalaci více než jedné verze aplikace pomocí technologie ClickOnce instalační program přesune předchozí verze aplikace do složky s názvem Archive v umístění pro publikování, které zadáte. Archivace předchozích verzí tímto způsobem udržuje instalační adresář v nejasnosti od předchozí verze.

### <a name="to-specify-a-publishing-location"></a>Určení umístění pro publikování

1. S projektem vybraným v **Průzkumník řešení**v nabídce **projekt** klikněte na **vlastnosti**.

2. Klikněte na kartu **publikovat** .

3. Do pole **umístění pro publikování** zadejte umístění pro publikování pomocí jednoho z následujících formátů:

   - Pokud chcete publikovat do sdílené složky nebo cesty k disku, zadejte cestu buď pomocí cesty UNC ( \\ \Server\ApplicationName), nebo cesty k souboru (C:\Deploy\ApplicationName).

   - Pokud chcete publikovat na server FTP, zadejte cestu pomocí formátu FTP: \/ /FTP.Microsoft.com/ApplicationName.

     Všimněte si, že text musí být přítomen v poli **umístění pro publikování** , aby tlačítko Procházet (**...**) fungovalo.

## <a name="see-also"></a>Viz také
 [Publikování aplikací ClickOnce](../deployment/publishing-clickonce-applications.md) [Postupy: publikování aplikace ClickOnce pomocí Průvodce publikováním](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
