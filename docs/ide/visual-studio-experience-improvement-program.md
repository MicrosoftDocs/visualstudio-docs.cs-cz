---
title: Program Zlepšování softwaru a služeb na základě zkušeností uživatelů
description: Přečtěte si, jak spravovat nastavení ochrany osobních údajů v sadě Visual Studio.
ms.date: 05/21/2018
ms.topic: conceptual
author: PoulChapman
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b6c785b755b64f0dd7e367a01d9c05c1981ea558
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "71693017"
---
# <a name="visual-studio-customer-experience-improvement-program"></a>Program Zlepšování softwaru a služeb na základě zkušeností uživatelů pro Visual Studio

Program Zlepšování softwaru a služeb na základě zkušeností uživatelů sady Visual Studio (VSCEIP) je navržen tak, aby společnosti Microsoft pomohl v průběhu času vylepšit sadu Visual Studio. Tento program [shromažďuje informace o chybách](../ide/diagnostic-data-collection.md), počítačovém hardwaru a způsobu, jakým uživatelé používají aplikaci Visual Studio, aniž by uživatelé přerušili jejich úlohy v počítači. Shromážděné informace pomáhají společnosti Microsoft určit, které funkce je třeba zlepšit. Tento dokument se zabývá tím, jak se přihlásit nebo z programu VSCEIP.

[!INCLUDE [gdpr-hybrid-note](../misc/includes/gdpr-hybrid-note.md)]
> [!NOTE]
> Nastavení vscefraku pro přihlášení nebo odhlášení se nevztahují na nastavení nahlášení problému v sadě Visual Studio. Když nahlásíte protokoly problémů, jsou shromažďovány a odesílány společnosti Microsoft pouze v případě, že poskytnete oprávnění kliknutím na tlačítko Odeslat. Máte-li zájem o správu protokolů před odesláním do "Nahlásit problém", přečtěte si prosím [feedback privacy](./developer-community-privacy.md) pro více informací.

## <a name="opt-in-or-out"></a>Přihlásit se nebo odhlásit

VSCEIP je ve výchozím nastavení zapnutý. Můžete jej vypnout nebo znovu zapnout podle následujících pokynů:

1. V sadě Visual Studio zvolte **Nápověda** > **k odeslání zpětné vazby**a pak vyberte **Nastavení**.

   Otevře se dialogové okno **Visual Studio Experience Improvement Program.**

1. Chcete-li se odhlásit, vyberte **možnost Ne, nechtěl bych se zúčastnit**a pak vyberte **možnost OK**. Chcete-li se přihlásit, vyberte **možnost Ano, jsem ochoten se zúčastnit**a pak vyberte **možnost OK**.

   ![Dialogové okno Program zlepšování prostředí visual studio](media/experience-improvement-program.png)

### <a name="registry-settings"></a>Nastavení registru

Pokud nainstalujete [nástroje pro sestavení sady Visual Studio](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2017), je nutné aktualizovat registr a nakonfigurovat protokol VSCEIP. Podnikoví zákazníci mohou vytvořit zásady skupiny pro přihlášení nebo odhlášení z programu VSCEIP nastavením zásad založených na registru.

Příslušný klíč registru a nastavení jsou následující:

::: moniker range="vs-2017"

- V 64bitovém osu klíč = **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\VSCommon\15.0\SQM**
- V 32bitovém osu klíč = **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSCommon\15.0\SQM**
- Pokud jsou povoleny zásady skupiny, klíč = **HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\VisualStudio\SQM**

::: moniker-end

::: moniker range=">=vs-2019"

- V 64bitovém osu klíč = **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\VSCommon\16.0\SQM**
- V 32bitovém osu klíč = **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSCommon\16.0\SQM**
- Pokud jsou povoleny zásady skupiny, klíč = **HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\VisualStudio\SQM**

::: moniker-end

Vstup = **Optin**

Hodnota = (DWORD)

- **0** je odhlásila (vypněte VSCEIP)
- **1** je přihlášen (zapněte VSCEIP)

> [!CAUTION]
> Pokud chybně upravíte registr, může dojít k vážnému poškození systému. Před provedením změn v registru doporučujeme zálohovat všechna důležitá data v počítači. Možnost spuštění **poslední známé funkční konfigurace** můžete také použít, pokud narazíte na problémy po použití ručních změn.

Další informace o informacích shromážděných, zpracovávaných nebo přenášených programem VSCEIP naleznete v [Prohlášení společnosti Microsoft o zásadách ochrany osobních údajů](https://privacy.microsoft.com/privacystatement).

## <a name="see-also"></a>Viz také

* [Diagnostické informace shromažďované visual studio](diagnostic-data-collection.md)
* [Možnosti zpětné vazby sady Visual Studio](../ide/feedback-options.md)
* [Jak nahlásit problém s Visual Studio](../ide/how-to-report-a-problem-with-visual-studio.md)
* [Komunita vývojářů visual studia](https://developercommunity.visualstudio.com/)
* [Prohlášení společnosti Microsoft o zásadách ochrany osobních údajů](https://privacy.microsoft.com/privacystatement)
