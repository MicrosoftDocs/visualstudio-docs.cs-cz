---
title: Výjimka ze systému Windows Information Protection
ms.date: 06/01/2018
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8b4eb454f641b5bef7273464d605fb194f650790
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "75588561"
---
# <a name="configure-visual-studio-as-a-wip-exempt-app"></a>Konfigurace sady Visual Studio jako aplikace s výjimkou nedokončené výroby

[Windows Information Protection](/windows/security/information-protection/windows-information-protection/protect-enterprise-data-using-wip) (NV) pomáhá chránit podniková data před únikem aplikací, jako jsou e-mail, sociální média a veřejný cloud, které jsou mimo podniková řízení. Nedokončená výroba pomáhá chránit před náhodnými úniky dat na zařízeních vlastněných podnikem a na osobních zařízeních, aniž by se musely měnit vaše prostředí nebo jiné aplikace.

Očekává se, že aplikace *podporou* pro nedokončenou výrobu budou bránit podnikovým datům v nechráněných síťových umístěních a nebude se šifrovat osobní údaje. Visual Studio není aplikace podporou, takže nefunguje v prostředí s povolenými nedokončenými výrobou, pokud ji nechcete vyloučit. Použijte postup v tomto článku, pokud chcete, aby aplikace Visual Studio fungovala na počítači s podporou nedokončené výroby.

## <a name="configure-vs-as-a-wip-exempt-app"></a>Konfigurace VS as a aplikace s výjimkou nedokončené výroby

Aplikaci Visual Studio můžete vyloučit z omezení nedokončené výroby, ale pořád jim umožní používat podniková data. Aplikace s výjimkou nedokončené výroby se můžou připojovat k prostředkům v podnikovém cloudu pomocí IP adresy nebo názvu hostitele. Nepoužívá se žádné šifrování a aplikace má přístup k místním souborům.

Pokud chcete aplikaci Visual Studio vyloučit z nedokončené výroby, postupujte podle [kroků pro vyloučení desktopové aplikace](/windows/security/information-protection/windows-information-protection/create-wip-policy-using-intune-azure#exempt-apps-from-a-wip-policy).

## <a name="create-a-wip-exempt-applocker-policy-file"></a>Vytvořit soubor zásad AppLockeru s výjimkou nedokončených výrob

Vzhledem k tomu, že Visual Studio obsahuje více binárních souborů, [vytvořte soubor zásad AppLockeru bez NEdokončené výroby](/windows/security/threat-protection/windows-defender-application-control/applocker/run-the-automatically-generate-rules-wizard). AppLocker umožňuje automaticky generovat pravidla pro všechny soubory ve složce.

## <a name="add-appcompat-to-the-enterprise-cloud-resource-policy"></a>Přidání AppCompat do zásad podnikového cloudového prostředku

Chcete-li určit, kam má aplikace Visual Studio přistupovat k podnikovým datům ve vaší síti, postupujte podle těchto [kroků a definujte, kam mohou chráněné aplikace najít a odeslat podniková data](/windows/security/information-protection/windows-information-protection/create-wip-policy-using-intune-azure#choose-where-apps-can-access-enterprise-data). Pokud chcete systému Windows zabránit v blokování připojení ke cloudovým prostředkům prostřednictvím IP adresy, nezapomeňte do nastavení přidat \* řetězec/AppCompat \* /.

## <a name="see-also"></a>Viz také

- [Chování aplikace s nedokončenou výrobou](/windows/security/information-protection/windows-information-protection/app-behavior-with-wip)
