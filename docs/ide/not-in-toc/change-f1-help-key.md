---
title: Změna klíče Nápověda F1
description: Popisuje, jak znovu namapovat nebo odebrat mapování kláves F1.
ms.date: 08/20/2020
ms.topic: how-to
ms.custom: contperf-fy21q1
robots: noindex,nofollow
manager: jmartens
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 30073b31fb98f604313c8de5d45687f3f768a374
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99961687"
---
# <a name="change-the-f1-help-key-in-visual-studio"></a>Změna klíče Nápověda F1 v aplikaci Visual Studio

Pokud chcete použít klávesu F1 pro jinou funkci než službu F1 Help, nebo pokud chcete jenom zakázat nápovědu pomocí klávesy F1, můžete mapování klíčů odebrat nebo upravit.

> [!IMPORTANT]
> Pokud chcete zakázat nápovědu F1 z důvodu problémů s výkonem, doporučujeme mapování klíče dočasně upravit, abyste mohli otestovat vylepšení služby Nápověda F1 v části aktualizace sady Visual Studio. Ve většině scénářů je F1 snadný způsob, jak otevřít referenční stránky pro klíčová slova jazyka a rozhraní API z editoru kódu nebo otevřít stránky s nápovědu související s Windows nebo prvky uživatelského rozhraní v integrovaném vývojovém prostředí (IDE). Pokud ho zakážete, zakážete ho pro všechna použití v rámci sady Visual Studio.

**Zakázání Nápověda F1:**

1. V aplikaci Visual Studio vyberte   >  **Možnosti** nástrojů a potom v části **prostředí** vyberte **klávesnice**.

1. V textovém poli **Zobrazit příkazy obsahující** textové pole zadejte **help. F1** pro filtrování zobrazení příkazů.

   ![Zakázat nápovědu F1](../not-in-toc/media/disable-f1-help-key.png)

1. Výběrem **Odebrat** odeberte mapování klíče.

1. Vyberte textové pole stiskněte klávesovou **zkratku** .

1. Na klávesnici stiskněte novou kombinaci kláves nebo kláves pro nápovědu F1, jako je **Alt + F1**, vyberte **přiřadit** a pak vyberte **OK**.

Další informace o nastavení klávesových zkratek najdete v tématu [identifikace a přizpůsobení klávesových zkratek](../../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).
