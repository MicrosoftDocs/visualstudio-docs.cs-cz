---
title: Zadejte umístění, ze kterého se budou koncoví uživatelé instalovat.
description: Naučte se, jak nastavit vlastnost URL instalace, která je hostitelem publikované aplikace ClickOnce pro instalaci.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3518a2eef331414e5c73c0cebb36681ad2b72d61
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2020
ms.locfileid: "94349617"
---
# <a name="how-to-specify-the-location-where-end-users-will-install-from"></a>Postupy: určení umístění, z něhož budou koncoví uživatelé instalovat

Při publikování [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace není umístění, kde uživatelé najdou ke stažení a instalaci aplikace, nutně umístění, kam aplikaci poprvé publikujete. V některých organizacích může vývojář například publikovat aplikaci na přípravném serveru a potom Správce přesune aplikaci na webový server.

V takovém případě můžete použít `Installation URL` vlastnost k určení webového serveru, kde budou uživatelé stahovat aplikaci. To je nezbytné, aby manifest aplikace věděl, kde hledat aktualizace.

`Installation URL`Vlastnost lze nastavit na stránce **publikovat** v **Návrháři projektu**.

> [!NOTE]
> `Installation URL`Vlastnost lze také nastavit pomocí **PublishWizard**. Další informace naleznete v tématu [How to: Publish a aplikace ClickOnce using the Publish Wizard](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).

### <a name="to-specify-an-installation-url"></a>Určení instalační adresy URL

1. S projektem vybraným v **Průzkumník řešení** v nabídce **projekt** klikněte na **vlastnosti**.

2. Klikněte na kartu **publikovat** .

3. V poli Adresa URL instalace zadejte umístění instalace pomocí plně kvalifikované adresy URL ve formátu `https://www.contoso.com/ApplicationName` nebo cesty UNC ve formátu `\Server\ApplicationName` .

## <a name="see-also"></a>Viz také
- [Postupy: určení umístění, kam aplikace Visual Studio kopíruje soubory](../deployment/how-to-specify-where-visual-studio-copies-the-files.md)
- [Publikování aplikací ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Postupy: publikování aplikace ClickOnce pomocí Průvodce publikováním](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)