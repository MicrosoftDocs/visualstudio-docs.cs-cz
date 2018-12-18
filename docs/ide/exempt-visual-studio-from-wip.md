---
title: Vyloučení ze služby Windows Information Protection
ms.date: 06/01/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1a1b38e6e30a816382da72ef8280868fa68dfb10
ms.sourcegitcommit: ce154aee5b403d5c1c41da42302b896ad3cf8d82
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/07/2018
ms.locfileid: "34845893"
---
# <a name="configure-visual-studio-as-a-wip-exempt-app"></a>Konfigurace Visual Studia jako aplikaci vyloučená probíhající práce

[Služba Windows Information Protection](/windows/security/information-protection/windows-information-protection/protect-enterprise-data-using-wip) (NV) pomáhá chránit podniková data, abyste zabránili úniku prostřednictvím aplikace, jako je e-mail, sociální média a veřejný cloud, které jsou mimo kontrolu příslušného podniku. Probíhající práce pomáhá chránit před úniky náhodných dat na zařízeních ve vlastnictví společnosti a osobních zařízení bez nutnosti změny prostředí nebo ostatních aplikací.

*Kompatibilních* aplikací pro probíhající práce se očekává zabránit podniková data přejdete do nechráněných síťových umístění a vyhnout se šifrování osobní data. Visual Studio není vylepšené aplikace, tak nebude fungovat v prostředí podporujícího probíhající práce, pokud jste ji vyloučit. Postupujte podle kroků v tomto článku povolit Visual Studio pro funkce na počítači povolené probíhající práce.

## <a name="configure-vs-as-a-wip-exempt-app"></a>Nakonfigurovat VS jako aplikaci vyloučená probíhající práce

Můžete vyloučit z omezení probíhající práce Visual Studio, ale stále povolit ho na použití podniková data. Probíhající práce vyloučená aplikace můžou připojovat k podnikové cloudové prostředky pomocí IP adresu nebo název hostitele. Žádné šifrování se použije, a aplikace přístup k místním souborům.

Pokud chcete vyloučit z NV Visual Studio, postupujte [kroky k vyjmutí aplikace na ploše](/windows/security/information-protection/windows-information-protection/create-wip-policy-using-intune-azure#exempt-apps-from-a-wip-policy).

## <a name="create-a-wip-exempt-applocker-policy-file"></a>Vytvořte soubor zásad Applockeru vyloučená probíhající práce

Vzhledem k tomu, že sada Visual Studio obsahuje několik binární soubory, [vytvořit soubor zásad Applockeru NV vyloučená](/windows/security/threat-protection/windows-defender-application-control/applocker/run-the-automatically-generate-rules-wizard). AppLocker umožňuje automaticky generovat pravidla pro všechny soubory ve složce.

## <a name="add-appcompat-to-the-enterprise-cloud-resource-policy"></a>Přidání kompatibility aplikace do zásad prostředků cloudu Enterprise

Chcete-li určit, kde jsou pro Visual Studio přístupem k podnikovým datům ve vaší síti, postupujte podle těchto [kroky k definování kde chráněné aplikace můžete najít a odeslat podniková data](/windows/security/information-protection/windows-information-protection/create-wip-policy-using-intune-azure#choose-where-apps-can-access-enterprise-data). Pokud chcete zastavit Windows blokovat připojení ke cloudovým prostředkům prostřednictvím IP adresu, nezapomeňte přidat nebo\*kompatibility aplikace\*/ řetězec nastavení.

## <a name="see-also"></a>Viz také:

- [Chování aplikace s probíhající práce](/windows/security/information-protection/windows-information-protection/app-behavior-with-wip)