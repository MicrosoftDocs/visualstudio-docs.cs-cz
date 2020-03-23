---
title: Výjimka z ochrany informací systému Windows
ms.date: 06/01/2018
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8b4eb454f641b5bef7273464d605fb194f650790
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75588561"
---
# <a name="configure-visual-studio-as-a-wip-exempt-app"></a>Konfigurace sady Visual Studio jako aplikace vynětí nedokončené výroby

[Ochrana informací systému Windows](/windows/security/information-protection/windows-information-protection/protect-enterprise-data-using-wip) (WIP) pomáhá chránit podniková data před únikem prostřednictvím aplikací, jako jsou e-maily, sociální média a veřejný cloud, které jsou mimo kontrolu podniku. Wip pomáhá chránit před náhodným únikem dat na podnikových zařízeních a osobních zařízeních, aniž by bylo nutné změnit vaše prostředí nebo jiné aplikace.

Očekává se, že *osvícené* aplikace pro nedokončenou výrobu nedokončené výroby zabrání tomu, aby podniková data přechází do nechráněných síťových umístění, a aby se zabránilo šifrování osobních dat. Visual Studio není osvícená aplikace, takže nefunguje v prostředích s podporou WIP, pokud ji nevyjmete. Podle kroků v tomto článku povolte Visual Studio fungovat v počítači s podporou wip.

## <a name="configure-vs-as-a-wip-exempt-app"></a>Konfigurace VS jako aplikace vynětí nedokončené výroby

Visual Studio můžete vyjmout z omezení nV, ale přesto povolit použití podnikových dat. Aplikace vynětí nedokončené výroby se můžou k prostředkům podnikového cloudu připojit pomocí IP adresy nebo názvu hostitele. Není použito žádné šifrování a aplikace má přístup k místním souborům.

Pokud chcete visual studio vyjmout z nedokončené výroby, postupujte [tak, že osvobodíte desktopovou aplikaci](/windows/security/information-protection/windows-information-protection/create-wip-policy-using-intune-azure#exempt-apps-from-a-wip-policy).

## <a name="create-a-wip-exempt-applocker-policy-file"></a>Vytvoření souboru zásad nástroje AppLocker s výjimkou služby Wip

Vzhledem k tomu, že Visual Studio obsahuje více binárních souborů, [vytvořte soubor zásad AppLocker osvobozený od nedokončené výroby](/windows/security/threat-protection/windows-defender-application-control/applocker/run-the-automatically-generate-rules-wizard). AppLocker umožňuje automaticky generovat pravidla pro všechny soubory ve složce.

## <a name="add-appcompat-to-the-enterprise-cloud-resource-policy"></a>Přidání appcompatu do zásad podnikových cloudových prostředků

Chcete-li určit, kde má Visual Studio přístup k podnikovým datům ve vaší síti, [definujte, kde mohou chráněné aplikace najít a odeslat podniková data](/windows/security/information-protection/windows-information-protection/create-wip-policy-using-intune-azure#choose-where-apps-can-access-enterprise-data). Chcete-li zabránit systému Windows v blokování připojení ke cloudovým prostředkům prostřednictvím IP adresy, nezapomeňte do nastavení přidat řetězec /\*AppCompat\*/ string.

## <a name="see-also"></a>Viz také

- [Chování aplikace s nedokončenou nedokončenou hodnotou](/windows/security/information-protection/windows-information-protection/app-behavior-with-wip)
