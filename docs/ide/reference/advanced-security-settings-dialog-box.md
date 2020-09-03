---
title: Dialogové okno Upřesnit nastavení zabezpečení
ms.date: 06/27/2018
ms.technology: vs-ide-deployment
ms.topic: reference
f1_keywords:
- vs.err.debug_in_zone_no_hostproc
helpviewer_keywords:
- Advanced Security Settings dialog box
ms.assetid: 2e7aefe9-6d20-4f3e-b257-aee1ebcc6f5d
author: Mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5d34d1b16f36c90f4200a091050d1646fc563d33
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85419078"
---
# <a name="advanced-security-settings-dialog-box"></a>dialogové okno Upřesnit nastavení zabezpečení

Toto dialogové okno umožňuje zadat nastavení zabezpečení související s laděním v zóně.

![Dialogové okno Upřesnit nastavení zabezpečení v aplikaci Visual Studio](../media/advanced-security-settings.png)

Chcete-li získat přístup k tomuto dialogovému oknu, vyberte uzel projektu v **Průzkumník řešení**a potom v nabídce **projekt** klikněte na příkaz **vlastnosti**. Když se zobrazí **Návrhář projektu** , klikněte na kartu **zabezpečení** . Na stránce **zabezpečení** vyberte **Povolit nastavení zabezpečení ClickOnce**, klikněte na **Toto je aplikace s částečným vztahem důvěryhodnosti**a pak klikněte na **Upřesnit**.

## <a name="uielement-list"></a>UIElement – seznam

**Udělit aplikaci přístup k jejímu původnímu umístění**

Pokud zaškrtnete toto políčko, aplikace bude mít přístup k webu nebo ke sdílené složce na serveru, na které je publikovaná. Tato možnost je vybrána ve výchozím nastavení.

**Ladit tuto aplikaci, jako kdyby byla stažena z následující adresy URL**

Pokud je nutné, aby aplikace získala přístup k webu nebo ke sdílené složce na serveru, která odpovídá **instalační adrese URL** zadané na stránce **publikování** , zadejte tuto adresu URL sem. Tato možnost je k dispozici pouze v případě, že je vybrána možnost **udělit aplikaci přístup k jejímu webu původu** .

## <a name="see-also"></a>Viz také

- [Stránka Zabezpečení, návrhář projektu](../../ide/reference/security-page-project-designer.md)
