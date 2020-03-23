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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 033c8d9c97d54b972a7bf30e9e1e04171e5b505e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595836"
---
# <a name="advanced-security-settings-dialog-box"></a>dialogové okno Upřesnit nastavení zabezpečení

Toto dialogové okno umožňuje určit nastavení zabezpečení související s laděním v zóně.

![Dialogové okno Upřesnit nastavení zabezpečení v sadě Visual Studio](../media/advanced-security-settings.png)

Chcete-li získat přístup k tomuto dialogovému oknu, vyberte uzel projektu v **Průzkumníku řešení**a v nabídce **Project** klepněte na příkaz **Vlastnosti**. Po zobrazení **Návrháře projektů** klikněte na kartu **Zabezpečení.** Na stránce **Zabezpečení** vyberte **možnost Povolit nastavení zabezpečení ClickOnce**, klepněte na **položku Toto je aplikace s částečnou důvěryhodností**a potom klepněte na tlačítko **Upřesnit**.

## <a name="uielement-list"></a>Seznam Prvků UI

**Udělit aplikaci přístup k místu původu**

Pokud toto políčko zaškrtnete, bude mít aplikace přístup k webu nebo sdílené složce serveru, na které je publikována. Tato možnost je vybrána ve výchozím nastavení.

**Ladění této aplikace, jako by byla stažena z následující adresy URL**

Pokud je nutné povolit aplikaci přístup k webu nebo sdílené straně serveru odpovídající **adrese URL instalace,** kterou jste zadali na stránce **Publikovat,** zadejte tuto adresu URL zde. Tato možnost je k dispozici pouze v případě, že je **vybrána možnost Udělit aplikaci přístup k webu původu.**

## <a name="see-also"></a>Viz také

- [Stránka Zabezpečení, Návrhář projektu](../../ide/reference/security-page-project-designer.md)
