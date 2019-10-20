---
title: Dialogové okno Upřesnit nastavení zabezpečení | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.err.debug_in_zone_no_hostproc
- vs.err.debug_in_zone_no_hostproc:11310
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Advanced Security Settings dialog box
ms.assetid: 2e7aefe9-6d20-4f3e-b257-aee1ebcc6f5d
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 000c3c4e2996869e96fd0d6097b5bab8576936a7
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651742"
---
# <a name="advanced-security-settings-dialog-box"></a>Dialogové okno Upřesnit nastavení zabezpečení
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Toto dialogové okno umožňuje zadat nastavení zabezpečení související s laděním v zóně.

 Chcete-li získat přístup k tomuto dialogovému oknu, vyberte uzel projektu v **Průzkumník řešení**a potom v nabídce **projekt** klikněte na příkaz **vlastnosti**. Když se zobrazí **Návrhář projektu** , klikněte na kartu **zabezpečení** . Na stránce **zabezpečení** vyberte **Povolit nastavení zabezpečení ClickOnce**, klikněte na **Toto je aplikace s částečným vztahem důvěryhodnosti**a pak klikněte na **Upřesnit**.

## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní
 **Ladit tuto aplikaci s vybranou sadou oprávnění** Pokud zaškrtnete toto políčko, sada oprávnění vybraná na stránce **zabezpečení** se použije při ladění. Ve výchozím nastavení je tato možnost vybraná.

 Aby ladění v zóně zabezpečení fungovalo, musí být tato možnost povolená. také je nutné povolit možnost **hostující proces hostování sady Visual Studio** (k dispozici na stránce **ladění** v **Návrháři projektu**).

 Pro projekty aplikace webového prohlížeče WPF je zaškrtnuto a zakázáno možnost **Ladit tuto aplikaci s vybranou sadou oprávnění** .

 **Udělit aplikaci přístup k jejímu původnímu umístění** Pokud zaškrtnete toto políčko, aplikace bude mít přístup k webovému serveru nebo ke sdílené složce na serveru, na které je publikovaná. Ve výchozím nastavení je tato možnost vybraná.

 **Ladit tuto aplikaci, jako kdyby byla stažena z následující adresy URL** Pokud je nutné, aby aplikace získala přístup k webu nebo sdílené složce na serveru, která odpovídá **instalační adrese URL** zadané na stránce **publikování** , zadejte tuto adresu URL sem. Tato možnost je k dispozici pouze v případě, že je vybrána možnost **udělit aplikaci přístup k jejímu webu původu** .

## <a name="see-also"></a>Viz také
 [Stránka Zabezpečení, Návrhář projektu](../../ide/reference/security-page-project-designer.md)
