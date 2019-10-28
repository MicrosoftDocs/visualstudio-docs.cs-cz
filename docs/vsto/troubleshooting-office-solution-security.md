---
title: Řešení potíží se zabezpečením řešení pro systém Office
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- security [Office development in Visual Studio], troubleshooting
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 289ffc3b5260260c9da8d0ec61e5c79890394802
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985552"
---
# <a name="troubleshoot-office-solution-security"></a>Řešení potíží se zabezpečením řešení pro systém Office
  Toto téma obsahuje tipy pro řešení běžných problémů, se kterými se můžete setkat při práci s zabezpečením řešení pro systém Office.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="trusted-solutions-cannot-be-installed-from-restricted-sites"></a>Důvěryhodná řešení nelze instalovat z lokalit s omezeným přístupem.
 Pokud je web uveden v zóně Servery s omezeným přístupem aplikace Internet Explorer, nemohou uživatelé instalovat řešení z webového umístění. To platí i v případě, že je řešení podepsané důvěryhodným certifikátem.

 Adresa URL manifestu nasazení může být rozdělená do jedné z pěti zón:

- Tento počítač

- Internet

- Místní intranet

- Důvěryhodné servery

- Servery s omezeným přístupem

  Pokud bylo umístění manifestu nasazení přiřazeno k zóně lokalit s omezeným přístupem, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] nenainstaluje řešení. Pokud je umístění známé a může být důvěryhodné, může uživatel odebrat umístění ze zóny servery s omezeným přístupem a nainstalovat řešení. Informace o tom, jak spravovat zóny, najdete v tématu [Konfigurace důvěryhodných vydavatelů ClickOnce](/previous-versions/dotnet/articles/ms996418(v=msdn.10)).

## <a name="solutions-cannot-be-installed-from-network-file-shares-or-web-locations-when-internet-explorer-enhanced-security-configuration-or-internet-explorer-7-is-installed"></a>Řešení nelze instalovat ze sdílených síťových složek nebo webových umístění, když je nainstalována konfigurace rozšířeného zabezpečení aplikace Internet Explorer nebo aplikace Internet Explorer 7.
 Konfigurace rozšířeného zabezpečení aplikace Internet Explorer (IEESC) v systému Windows Server 2003 a vyšší a Internet Explorer 7 a vyšší výrazně omezuje schopnost uživatelů procházet Internet. Když se uživatelé pokusí nainstalovat řešení Office ze sdílené síťové složky nebo webového umístění, může se zobrazit následující chybová zpráva: "přizpůsobené funkce v této aplikaci nebudou fungovat, protože certifikát použitý k podepsání manifestu nasazení pro  *Řešení* není důvěryhodné. O další pomoc požádejte správce. "

 Pokud je adresa URL manifestu nasazení zařazena do kategorie sítě Internet v IEESC a Internet Exploreru 7 a novějším, musí mít manifest certifikát od důvěryhodného vydavatele, jinak se řešení nedá nainstalovat. Bez IEESC je výchozím chováním vyzvat koncového uživatele k tomu, aby se rozhodlo o důvěryhodnosti.

 Chcete-li spravovat účinek IEESC a Internet Exploreru 7 a vyšší, identifikujte weby a cesty UNC (Universal Naming Convention), kterým důvěřujete, a přidejte je do jedné z důvěryhodných zón zabezpečení (místní intranet nebo důvěryhodné servery). Informace o tom, jak spravovat zóny, najdete v tématu [Konfigurace důvěryhodných vydavatelů ClickOnce](/previous-versions/dotnet/articles/ms996418(v=msdn.10)).

## <a name="see-also"></a>Viz také:
- [Zabezpečení řešení pro systém Office](../vsto/securing-office-solutions.md)
