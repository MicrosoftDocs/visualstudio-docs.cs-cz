---
title: Předprodukční inventář v předplatném sady Visual Studio | Visual Studio Marketplace
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: 7d74e113-8fb2-490e-8502-48cce7b1327a
ms.date: 03/19/2021
ms.topic: conceptual
description: Seznamte se s zodpovědností správců za účelem provádění předprodukčních inventářů.
ms.openlocfilehash: f6b1e1ebc02a986be86fb48578a4be47ccc3dfaa
ms.sourcegitcommit: d8d230791890cda532c263d04288dc13d2261c7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2021
ms.locfileid: "104757669"
---
# <a name="inventory-of-pre-production-environment"></a>Inventář předprodukčního prostředí
Předplatná sady Visual Studio zjednodušují správu prostředků, a to pomocí počítání uživatelů místo zařízení.

Správci sady Visual Studio musí přiřadit předplatná sady Visual Studio **konkrétním pojmenovaným jednotlivcům**. Konvence pojmenování, jako je například dev1, Dev2 nebo použití názvů týmů, jako je "FeatureTeam", nejsou **povoleny**.

Tady je několik způsobů, jak zjednodušit inventarizaci předprodukčního prostředí:
- Zkontrolujte přiřazení uživatelů. Společnost Microsoft poskytuje web s názvem [portál pro správu sady Visual Studio](https://manage.visualstudio.com/) , který vám může pomáhat sledovat přiřazení předplatných sady Visual Studio.
- K vypsání uživatelů můžete použít místní nebo cloudovou službu Active Directory. Pokud ke správě přístupu uživatelů používáte službu Active Directory, možná budete moct identifikovat vývojové a testovací uživatele podle jejich členství v adresáři.
- Pro inventarizaci systémů použijte automatizované nástroje. Je také možné, že budete muset použít nástroj inventáře softwaru, který vám umožní spravovat softwarové prostředky a rozlišovat předprodukční prostředí z produkčních prostředí. Mnoho zákazníků s Microsoft System Center vytvoří konvence pro pojmenování, které vám pomůžou automatizovat tuto část procesu inventarizace.
- Získejte nápovědu k ručnímu odsouhlasení. Zařadíte své zaměstnance, který vám umožní sjednotit vývoj a testování uživatelů pomocí vývojového a testovacího prostředí.

> [!NOTE]
> Software předplatných sady Visual Studio není licencován pro produkční prostředí, včetně jakéhokoli prostředí, ke kterému mají koncoví uživatelé k dispozici více než testování přijetí nebo zpětnou vazbu, prostředí připojující se k provozní databázi, podporu zotavení po havárii nebo zálohování v provozu nebo využité pro produkční prostředí během období špičky aktivity. Mezi tyto výjimky patří konkrétní výhody pro určité úrovně předplatného, které jsou uvedené v [dokumentu White Paper licencování sady Visual Studio](https://aka.ms/vslicensing).  

## <a name="resources"></a>Prostředky
- [Dokument white paper k licencování sady Visual Studio](https://visualstudio.microsoft.com/wp-content/uploads/2019/06/Visual-Studio-Licensing-Whitepaper-May-2019.pdf)
- [Podpora předplatných sady Visual Studio](https://aka.ms/vsadminhelp)
- [Multilicenční podmínky](https://www.microsoft.com/licensing/product-licensing/products.aspx)

## <a name="see-also"></a>Viz také
- [Dokumentace k sadě Visual Studio](/visualstudio/)
- [Dokumentace k Azure DevOps](/azure/devops/)
- [Dokumentace k Azure](/azure/)
- [Dokumentace k Microsoft 365](/microsoft-365/)

## <a name="next-steps"></a>Další kroky
Další informace o zodpovědnostech pro správce:
- [Odpovědnosti správce](admin-responsibilities.md)
- [Správa velkých týmů a externích dodavatelů](manage-teams.md)
- [Sledování přiřazení uživatelů a zpracování objednávek](assignments-orders.md)
- Použití [maximálního využití](maximum-usage.md) ke sledování závazků nákupu