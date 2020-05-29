---
title: Zvýhodnění virtuálních počítačů Microsoft Windows v předplatných sady Visual Studio | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 872c5746-5357-4764-949b-aa525a0adf1a
ms.date: 04/20/2020
ms.topic: conceptual
description: Zjistěte, jak můžete využít výhod virtuálního klienta Microsoft Windows prostřednictvím předplatného sady Visual Studio.
ms.openlocfilehash: b84527f7bdaf3e9218585bd52af0743ef23a5637
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/29/2020
ms.locfileid: "84183584"
---
# <a name="access-windows-virtual-desktop-in-subscriptions"></a>Přístup k virtuálnímu počítači s Windows v předplatných 
Předplatitelé sady Visual Studio teď můžou využívat svoje jednotlivé kredity Azure pro vývoj/testování pro služby Microsoft Windows Virtual Desktop.  
Virtuální počítač s Windows je komplexní služba virtualizace plochy a aplikací spuštěná v cloudu. Je to jediná infrastruktura virtuálních klientských počítačů (VDI), která nabízí zjednodušenou správu, Windows 10 s více relacemi, optimalizace pro Office 365 ProPlus a podporu pro prostředí vzdálené plochy (RDS). Nasaďte a škálujte stolní počítače a aplikace Windows v Azure během několika minut a Získejte integrované funkce zabezpečení a dodržování předpisů.
Tady je seznam toho, co můžete udělat při spuštění virtuální plochy Windows v Azure:
- Nastavení nasazení s více relacemi s Windows 10, které poskytuje plnou sadu Windows 10 s škálovatelností
- Virtualizujte Office 365 ProPlus a optimalizujte pro spouštění ve virtuálních scénářích s více uživateli.
- Poskytněte virtuálním klientům Windows 7 bezplatné rozšířené aktualizace zabezpečení.
- Přenesení stávajících klientských počítačů a aplikací pro vzdálenou plochu (RDS) a Windows serveru do libovolného počítače
- Virtualizujte desktopy i aplikace
- Správa stolních počítačů a aplikací Windows 10, Windows Server a Windows 7 s jednotným prostředím pro správu Další informace o tom, co můžete dělat s virtuálním počítačem s Windows, najdete v [úvodním videu](https://docs.microsoft.com/azure/virtual-desktop/overview).

## <a name="use-windows-virtual-desktop-with-azure"></a>Použití virtuální plochy Windows s Azure 
Předplatitelé sady Visual Studio teď mají několik způsobů použití předplatných Azure k placení za služby Windows Virtual Desktop:
- [Jednotlivé kredity Azure DevTest](vs-azure.md).  Předplatitelé, kteří přijímají jednotlivé kredity Azure DevTest v rámci svých předplatných, můžou tyto kredity využít k placení služby Windows Virtual Desktop.  Množství měsíčního kreditu závisí na úrovni předplatného.
- [Předplatné Azure DevTest](vs-azure-payg.md)s průběžnými platbami.  Vytvořením předplatných Azure a připojením platebního nástroje zajistíte plynulý způsob platby za využití virtuálních počítačů s Windows. 
- [Nabídka Azure smlouva Enterprise DevTest](azure-ea-devtest.md)  V rámci této nabídky můžou předplatitelé se smlouvou Enterprise platit za službu Virtual Desktop pro Windows s Azure za zlevněné ceny. 

## <a name="requirements"></a>Požadavky
Virtuální počítač s Windows vyžaduje službu Azure Active Directory (Azure AD), ke které se virtuální počítače připojí.  Uživatelé musí být členy této služby Azure AD.  Existují dvě možnosti implementace služby Azure AD:
- Adresářové služby Azure AD.  U většiny uživatelů se jedná o možnost snazší implementace.
- Virtuální počítač, na kterém běží řadič domény, může být propagační.  Tato možnost vyžaduje více práce, aby bylo možné nastavení, ale nabízí většině uživatelů nižší provozní náklady.
Úplný seznam požadavků na používání služby Virtual Desktop systému Windows najdete na [stránce s přehledem](https://docs.microsoft.com/azure/virtual-desktop/overview#requirements)virtuálního počítače s Windows. 

## <a name="get-started"></a>Začínáme 
Pokud jsou splněné všechny požadavky, budete chtít provést několik akcí, abyste mohli implementovat svou implementaci.  Pokud chcete začít, podívejte se na tyto kurzy:
- [Vytvoření tenanta virtuálních klientů Windows](https://docs.microsoft.com/azure/virtual-desktop/virtual-desktop-fall-2019/tenant-setup-azure-active-directory)
- [Vytvoření fondu hostitelů](https://docs.microsoft.com/azure/virtual-desktop/create-host-pools-azure-marketplace) pomocí Azure Portal
- [Správa skupin aplikací](https://docs.microsoft.com/azure/virtual-desktop/manage-app-groups) pro virtuální počítače s Windows

## <a name="eligibility"></a>Vznik
| Úroveň předplatného                                                 |     Kanály                                            | Výhoda                                                          | Mlčky?    |
|--------------------------------------------------------------------|---------------------------------------------------------|------------------------------------------------------------------|---------------|
| Visual Studio Enterprise (Standard)   | VL, Azure, Retail, | K dispozici|  Ano          |
| Visual Studio Enterprise s GitHubem Enterprise  | VL | K dispozici|  Ano          |
| Visual Studio Professional (Standard) | VL, Azure, Retail                                       | K dispozici                                                             |  Ano             |
| Visual Studio Professional s GitHubem Enterprise | VL                                       | K dispozici                                        |  Ano           |
| Visual Studio Test Professional (Standard)                         | VL, maloobchodní prodej                                              | K dispozici|  Ano          |
| MSDN Platforms (Standard)                                          | VL, maloobchodní prodej                                              | K dispozici                                         |  Ano          |
| Visual Studio Enterprise (Standard)  | NFR<sup>1</sup> |Není k dispozici  | – |
| Visual Studio Enterprise Visual Studio Professional (měsíční Cloud) | Azure | Není k dispozici | – |

<sup>1</sup>*zahrnuje: Not for Reprodej (NFR), FTE, (MVP), oblastní ředitel (RD), Microsoft Partner Network (MPN), Visual Studio Industry Partner (VSIP), Microsoft Certified Trainer, BizSpark, představte* si  

> [!NOTE]
> Společnost Microsoft už nenabízí Visual Studio Professional roční předplatné a Visual Studio Enterprise roční předplatné v cloudových předplatných. Stávající prostředí pro zákazníky se nijak nemění a možnost obnovit, zvýšit, snížit nebo zrušit jejich odběry. Novým zákazníkům doporučujeme přejít na [https://visualstudio.microsoft.com/vs/pricing/](https://visualstudio.microsoft.com/vs/pricing/) a prozkoumat různé možnosti nákupu sady Visual Studio.

Nejste si jistí, jaké Předplatné používáte?  Připojte se a [https://my.visualstudio.com/subscriptions](https://my.visualstudio.com/subscriptions?wt.mc_id=o~msft~docs) Zobrazte všechna předplatná přiřazená k vaší e-mailové adrese. Pokud nevidíte všechna Vaše předplatná, může být jedna nebo více přiřazená k jiné e-mailové adrese.  K zobrazení těchto předplatných se budete muset přihlásit pomocí této e-mailové adresy.

## <a name="see-also"></a>Viz také
- [Dokumentace k Azure](https://docs.microsoft.com/azure/)
- [Dokumentace k Windows Virtual Desktopu](https://docs.microsoft.com/azure/virtual-desktop/)

## <a name="next-steps"></a>Další kroky
-   Pokud potřebujete koupit předplatné sady Visual Studio, Projděte si:
     - [Ceny za maloobchodní nákupy](https://visualstudio.microsoft.com/vs/pricing/) prostřednictvím Microsoft Store
     - [Multilicenční programy](https://www.microsoft.com/licensing/default)
-   Další informace o [virtuálním počítači s Windows](https://docs.microsoft.com/azure/virtual-desktop/overview) 
