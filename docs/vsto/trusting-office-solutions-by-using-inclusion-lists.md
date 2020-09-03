---
title: Důvěryhodná řešení pro Office pomocí seznamů zahrnutí
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- permissions [Office development in Visual Studio]
- inclusion lists [Office development in Visual Studio], about inclusion lists
- security [Office development in Visual Studio], inclusion lists
- inclusion lists [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a4787831be31e2f91d668d4e3e7ca91496d7595a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72985548"
---
# <a name="trust-office-solutions-by-using-inclusion-lists"></a>Důvěryhodná řešení pro Office pomocí seznamů zahrnutí
  Seznamy zahrnutí umožňují uživatelům udělit vztah důvěryhodnosti k řešením Office, která jsou podepsaná certifikátem, který identifikuje vydavatele. Seznamy zahrnutí jsou specifické pro uživatele a dají se použít pro přizpůsobení na úrovni dokumentu a doplňky VSTO.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Když uživatel spustí řešení pro Office, kterému se pro daného uživatele neudělila důvěryhodnost, řešení systém Microsoft Office zobrazí dotaz na bezpečnostní rozhodnutí s [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] výzvou vztahu důvěryhodnosti. Pokud se uživatel rozhodne, že řešení důvěřuje, provede se vlastní nastavení a uživatel nebude příště vyzván k dalšímu spuštění.

## <a name="inclusion-list-and-windows-installer"></a>Seznam a Instalační služba systému Windows zahrnutí
 Instalace řešení Office do adresáře *Program Files* pomocí Instalační služba systému Windows vyžaduje oprávnění správce. V případě řešení pro systém Office v adresáři *Program Files* již modul runtime Visual Studio Tools for Office nekontroluje seznam zahrnutí, protože řešení pro systém Office již byla udělena oprávnění FullTrust.

## <a name="clickonce-trust-prompt"></a>Dotaz na vztah důvěryhodnosti pro ClickOnce
 Pomocí [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] implementace řešení pro systém Office můžou správci nakonfigurovat úroveň výzvy důvěryhodnosti, aby bylo možné zobrazovat výzvy, zakázat zobrazování výzev nebo vyžadovat důvěryhodný certifikát. Tato konfigurace se provádí pomocí klíče registru, který řídí přístup k seznamu zahrnutí.

 Pokud je dotazování zakázané, může být nainstalovaná jenom řešení s důvěryhodným a známým certifikátem. Pokud je úroveň výzvy nastavena na hodnotu Authenticode požadováno, řešení musí být podepsáno certifikátem ze známého úřadu, ale nevyžaduje certifikát, který je zřetězený s důvěryhodnou kořenovou autoritou (důvěryhodný certifikát). Pokud je povoleno dotazování, řešení by mohlo být podepsáno certifikátem s neznámou identitou. V tomto scénáři je rozhodnutí o důvěryhodnosti odloženo na koncového uživatele a dočasný certifikát by měl být pro instalaci řešení dostačující.

 Další informace najdete v tématech [How to: Configure a Security list Security](../vsto/how-to-configure-inclusion-list-security.md) a Table 2, s názvem "hodnoty klíče registru na úrovni výzvy spuštění" v tématu [Konfigurace důvěryhodných vydavatelů ClickOnce](/previous-versions/dotnet/articles/ms996418(v=msdn.10)).

## <a name="structure-of-the-inclusion-list"></a>Struktura seznamu zahrnutí
 Platná položka seznamu zahrnutí má dvě části: cestu k manifestu nasazení a veřejný klíč, který se používá k podepsání řešení. Po přidání řešení do seznamu zahrnutí se považuje za důvěryhodné. Po spuštění řešení Office aplikace systému Office porovná veřejný klíč v seznamu pro zahrnutí podpisovým klíčem v manifestu nasazení, aby ověřil, že aktuálně spuštěné řešení je stejné jako původní důvěryhodná verze.

## <a name="see-also"></a>Viz také
- [Udělení vztahu důvěryhodnosti řešením pro systém Office](../vsto/granting-trust-to-office-solutions.md)
- [Zabezpečení řešení pro systém Office](../vsto/securing-office-solutions.md)
