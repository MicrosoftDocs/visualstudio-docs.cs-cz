---
title: Výhody virtuální plochy microsoft windows v předplatných sady Visual Studio | Dokumenty společnosti Microsoft
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 872c5746-5357-4764-949b-aa525a0adf1a
ms.date: 04/20/2020
ms.topic: conceptual
description: Zjistěte, jak můžete využít výhod virtuální plochy Microsoft Windows prostřednictvím předplatného sady Visual Studio.
ms.openlocfilehash: 87911b1b7b6eb63eb85b64515d5d24755e4656e6
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649735"
---
# <a name="access-windows-virtual-desktop-in-subscriptions"></a>Přístup k virtuální ploše Windows v předplatných 
Předplatitelé Visual Studia teď mohou používat své kredity Azure pro vývoj a testování jednotlivých kreditů pro služby Microsoft Windows Virtual Desktop.  
Windows Virtual Desktop je komplexní služba virtualizace desktopů a aplikací spuštěná v cloudu. Jedná se o jedinou infrastrukturu virtuálních desktopů (VDI), která poskytuje zjednodušenou správu, vícerelační systém Windows 10, optimalizace pro Office 365 ProPlus a podporu prostředí Služby vzdálené plochy (RDS). Nasazujte a škálujte své plochy a aplikace windows v Azure během několika minut a získejte integrované funkce zabezpečení a dodržování předpisů.
Co můžete dělat při spuštění Windows Virtual Desktop v Azure:
- Nastavení nasazení windows 10 s více relacemi, které poskytuje kompletní Windows 10 se škálovatelností
- Virtualizace Office 365 ProPlus a optimalizace pro běh ve virtuálních scénářích pro více uživatelů
- Poskytněte virtuálním desktopům windows 7 bezplatné rozšířené aktualizace zabezpečení
- Přenesete stávající plochy vzdálené plochy (RDS) a plochy a aplikace systému Windows Server do libovolného počítače
- Virtualizace stolních počítačů i aplikací
- Správa ploch a aplikací pro Windows 10, Windows Server a Windows 7 pomocí jednotnésprávy Další informace o tom, co můžete dělat s Windows Virtual Desktop, se podívejte na [úvodní video](https://docs.microsoft.com/azure/virtual-desktop/overview).

## <a name="use-windows-virtual-desktop-with-azure"></a>Použití virtuální plochy Windows s Azure 
Předplatitelé Visual Studia teď mají několik způsobů, jak používat předplatná Azure k platbě za služby Windows Virtual Desktop:
- [Azure DevTest jednotlivé kredity](vs-azure.md).  Předplatitelé, kteří obdrží jednotlivé kredity Azure DevTest jako součást svých předplatných, můžou tyto kredity použít k platbě za služby Virtuální plochy Windows.  Výše měsíčního kreditu závisí na úrovni předplatného.
- [Předplatná Azure DevTest s průběžným platbou](vs-azure-payg.md)  Můžete vytvořit předplatná Azure a připojit platební nástroj, abyste měli bezproblémový způsob platby za využití virtuální plochy Windows. 
- [Nabídka Smlouvy Azure Enterprise DevTest](azure-ea-devtest.md).  Díky této nabídce mohou předplatitelé se smlouvami Enterprise platit za Virtuální plochu Windows pomocí Azure za zvýhodněné ceny. 

## <a name="requirements"></a>Požadavky
Virtuální plocha Windows vyžaduje Azure Active Directory (Azure AD), ke kterému se připojí virtuální počítače.  Uživatelé musí být členy tohoto azure ad.  Existuje dvě možnosti implementace Azure AD:
- Adresářové služby Azure AD.  Pro většinu uživatelů je to jednodušší možnost implementovat.
- Virtuální počítač se systémem promo řadič domény.  Tato možnost vyžaduje více práce k nastavení, ale nabízí většině uživatelů nižší provozní náklady.
Úplný seznam předpokladů pro používání programu Windows Virtual Desktop naleznete na [stránce přehledu](https://docs.microsoft.com/azure/virtual-desktop/overview#requirements)virtuální plochy systému Windows . 

## <a name="get-started"></a>Začínáme 
Když jsou všechny vaše požadavky na místě, budete chtít dokončit několik akcí, abyste svou implementaci zavedli.  Chcete-li začít, podívejte se na tyto výukové programy:
- [Vytvoření klienta virtuální plochy Windows](https://docs.microsoft.com/azure/virtual-desktop/tenant-setup-azure-active-directory)
- [Vytvoření fondu hostitelů](https://docs.microsoft.com/azure/virtual-desktop/create-host-pools-azure-marketplace) pomocí portálu Azure
- [Správa skupin aplikací](https://docs.microsoft.com/azure/virtual-desktop/manage-app-groups) pro Virtuální plochu Windows

## <a name="eligibility"></a>Způsobilosti
| Úroveň předplatného                                                 |     Kanály                                            | Výhoda                                                          | Obnovitelných zdrojů?    |
|--------------------------------------------------------------------|---------------------------------------------------------|------------------------------------------------------------------|---------------|
| Visual Studio Enterprise (standard)   | VL, Azure, Maloobchod, | K dispozici.|  Ano          |
| Visual Studio Enterprise s GitHub Enterprise  | Vl | K dispozici.|  Ano          |
| Visual Studio Professional (standard) | VL, Azure, Maloobchod                                       | K dispozici.                                                             |  Ano             |
| Visual Studio Professional s GitHub Enterprise | Vl                                       | K dispozici.                                        |  Ano           |
| Visual Studio Test Professional (standard)                         | VL, Maloobchod                                              | K dispozici.|  Ano          |
| Platformy MSDN (standardní)                                          | VL, Maloobchod                                              | K dispozici.                                         |  Ano          |
| Visual Studio Enterprise (standard)  | NFR<sup>1</sup> |Není k dispozici.  | – |
| Visual Studio Enterprise, Visual Studio Professional (měsíční cloud) | Azure | Není k dispozici. | – |

<sup>1</sup>  *Zahrnuje: Není pro další prodej (NFR), FTE, Nejhodnotnější Professional (MVP), Regionální ředitel (RD), Microsoft Partner Network (MPN), Visual Studio Průmysl Partner (VSIP), Microsoft Certified Trainer, BizSpark, Imagine*

> [!NOTE]
> Microsoft už nenabízí roční předplatná Visual Studio Professional a roční předplatná Visual Studia Enterprise v předplatných cloudu. Stávající zákazníci se nezmění a možnost obnovit, zvýšit, snížit nebo zrušit jejich odběry. Noví zákazníci se [https://visualstudio.microsoft.com/vs/pricing/](https://visualstudio.microsoft.com/vs/pricing/) doporučuje přejít na prozkoumat různé možnosti nákupu Visual Studio.

Nejste si jisti, které předplatné používáte?  Připojte [https://my.visualstudio.com/subscriptions](https://my.visualstudio.com/subscriptions?wt.mc_id=o~msft~docs) se k zobrazení všech předplatných přiřazených k vaší e-mailové adrese. Pokud nevidíte všechna předplatná, je možné, že máte jedno nebo více přiřazených k jiné e-mailové adrese.  Abyste se pomocí této e-mailové adresy zobcí, musíte se přihlásit pomocí této e-mailové adresy.

## <a name="see-also"></a>Viz také
- [Dokumentace k Azure](https://docs.microsoft.com/azure/)
- [Dokumentace k virtuální ploše systému Windows](https://docs.microsoft.com/azure/virtual-desktop/)

## <a name="next-steps"></a>Další kroky
-   Pokud potřebujete zakoupit předplatná Visual Studia, podívejte se na:
     - [Ceny za maloobchodní nákupy](https://visualstudio.microsoft.com/vs/pricing/) v obchodě Microsoft Store
     - [Multilicenční programy](https://www.microsoft.com/licensing/default)
-   Další informace o [virtuální ploše Windows](https://docs.microsoft.com/azure/virtual-desktop/overview) 
