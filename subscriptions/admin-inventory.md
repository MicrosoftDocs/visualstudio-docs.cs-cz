---
title: Inventář předprodukčních prostředí | Visual Studio Marketplace
author: evanwindom
ms.author: lank
manager: lank
ms.date: 07/23/2019
ms.topic: conceptual
description: Další informace o responsibilty správců pro provádění předprodukčních inventářů
ms.openlocfilehash: 8218b1802a6369aed00be63572c80cba7b5c29f3
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/10/2020
ms.locfileid: "75849826"
---
# <a name="inventory-of-pre-production-environment"></a>Inventář předprodukčního prostředí
Předplatná sady Visual Studio zjednodušují správu prostředků, a to pomocí počítání uživatelů místo zařízení.

Správci sady Visual Studio musí přiřadit předplatná sady Visual Studio **konkrétním pojmenovaným jednotlivcům**. Konvence pojmenování, jako je například dev1, Dev2 nebo použití názvů týmů, jako je "FeatureTeam", nejsou **povoleny**.

Tady je několik způsobů, jak zjednodušit inventarizaci předprodukčního prostředí:
- Zkontrolujte přiřazení uživatelů. Společnost Microsoft poskytuje web s názvem [portál pro správu sady Visual Studio](https://manage.visualstudio.com/) , který vám může pomáhat sledovat přiřazení předplatných sady Visual Studio.
- K vypsání uživatelů můžete použít místní nebo cloudovou službu Active Directory. Pokud ke správě přístupu uživatelů používáte službu Active Directory, možná budete moct identifikovat vývojové a testovací uživatele podle jejich členství v adresáři.
- Pro inventarizaci systémů použijte automatizované nástroje. Je také možné, že budete muset použít nástroj inventáře softwaru, který vám umožní spravovat softwarové prostředky a rozlišovat předprodukční prostředí z produkčních prostředí. Mnoho zákazníků s Microsoft System Center vytvoří konvence pro pojmenování, které vám pomůžou automatizovat tuto část procesu inventarizace.
- Získejte nápovědu k ručnímu odsouhlasení. Zařadíte své zaměstnance, který vám umožní sjednotit vývoj a testování uživatelů pomocí vývojového a testovacího prostředí.

## <a name="resources"></a>Prostředky
- [Dokument white paper k licencování sady Visual Studio](https://visualstudio.microsoft.com/wp-content/uploads/2019/06/Visual-Studio-Licensing-Whitepaper-May-2019.pdf)
- [Podpora správy a předplatných sady Visual Studio](https://visualstudio.microsoft.com/support/support-overview-vs)
- [Multilicenční podmínky](https://www.microsoft.com/licensing/product-licensing/products.aspx)

## <a name="next-steps"></a>Další kroky
Další informace o zodpovědnostech pro správce:
- [Odpovědnosti správce](admin-responsibilities.md)
- [Správa velkých týmů a externích dodavatelů](manage-teams.md)
- [Sledování přiřazení uživatelů a zpracování objednávek](assignments-orders.md)
- Použití [maximálního využití](maximum-usage.md) ke sledování závazků nákupu
