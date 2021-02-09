---
title: Program Zlepšování softwaru a služeb na základě zkušeností uživatelů
description: Zjistěte, jak spravovat nastavení ochrany osobních údajů v aplikaci Visual Studio.
ms.date: 05/21/2018
ms.topic: conceptual
author: PoulChapman
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 60a67da568703282a3ae469afa4dbc15c53cf4ba
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99873941"
---
# <a name="visual-studio-customer-experience-improvement-program"></a>Program Zlepšování softwaru a služeb na základě zkušeností uživatelů pro Visual Studio

Aplikace Visual Studio program Zlepšování softwaru a služeb na základě zkušeností uživatelů (VSCEIP) je navržena tak, aby pomohla Microsoftu v průběhu času zdokonalit Visual Studio. Tento program [shromažďuje informace o chybách](../ide/diagnostic-data-collection.md), hardwaru počítače a způsobu, jakým uživatelé používají aplikaci Visual Studio, aniž by přerušil uživatele v jejich úkolech v počítači. Shromážděné informace pomáhají společnosti Microsoft určit, které funkce se mají zlepšit. Tento dokument obsahuje informace o tom, jak vyjádřit nebo odhlásit VSCEIP.

[!INCLUDE [gdpr-hybrid-note](../misc/includes/gdpr-hybrid-note.md)]
> [!NOTE]
> Nastavení opt nebo out VSCEIP telemetrie neplatí pro nahlášení problému v aplikaci Visual Studio. Když zadáte zprávu o problémech, shromáždí se Microsoftu a pošle se společnosti Microsoft jenom po poskytnutí oprávnění kliknutím na Odeslat. Pokud vás zajímá Správa protokolů před odesláním do ' nahlášení problému ', přečtěte si informace o [ochraně osobních údajů pro zpětnou vazbu](./developer-community-privacy.md) .

## <a name="opt-in-or-out"></a>Výslovný souhlas nebo odhlášení

VSCEIP je ve výchozím nastavení zapnutý. Můžete ho zase zapnout nebo znovu spustit pomocí následujících pokynů:

1. V aplikaci Visual Studio zvolte možnost **help**  >  **Odeslat názor** a pak vyberte **Nastavení**.

   Otevře se dialogové okno **Program zlepšování sady Visual Studio na základě zkušeností uživatelů** .

1. Pokud se chcete odhlásit, vyberte **Ne,** nechci se zúčastnit a pak vyberte **OK**. Pokud se chcete přihlásit, vyberte **Ano, chci se zúčastnit** a pak vyberte **OK**.

   ![Dialog Program zlepšování sady Visual Studio na základě zkušeností uživatelů](media/experience-improvement-program.png)

### <a name="registry-settings"></a>Nastavení registru

Pokud nainstalujete [Nástroje sestavení pro Visual Studio](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2017), je nutné aktualizovat registr a nakonfigurovat VSCEIP. Podnikoví zákazníci mohou vytvořit zásady skupiny pro výslovný souhlas nebo odhlášení VSCEIP nastavením zásad založených na registru.

Relevantní klíč registru a nastavení jsou následující:

::: moniker range="vs-2017"

- V 64 operačním systému, Key = **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\VSCommon\15.0\SQM**
- V 32 operačním systému, Key = **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSCommon\15.0\SQM**
- Když je povolený Zásady skupiny, Key = **HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\VisualStudio\SQM**

::: moniker-end

::: moniker range=">=vs-2019"

- V 64 operačním systému, Key = **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\VSCommon\16.0\SQM**
- V 32 operačním systému, Key = **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSCommon\16.0\SQM**
- Když je povolený Zásady skupiny, Key = **HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\VisualStudio\SQM**

::: moniker-end

Vstup = **OptIn**

Value = (DWORD)

- **0** se odsouhlasí (vypnutí VSCEIP)
- **1** je výslovný souhlas (zapnout VSCEIP)

> [!CAUTION]
> Pokud chybně upravíte registr, může dojít k vážnému poškození systému. Před provedením změn v registru doporučujeme zálohovat všechna důležitá data v počítači. Pokud při použití ručních změn dojde k problémům, můžete použít také možnost při spuštění **Poslední známá funkční konfigurace** .

Další informace o informacích shromažďovaných, zpracovávaných nebo odeslaných službou VSCEIP naleznete v tématu [prohlášení o zásadách ochrany osobních údajů společnosti Microsoft](https://privacy.microsoft.com/privacystatement).

## <a name="see-also"></a>Viz také

* [Diagnostické informace shromažďované aplikací Visual Studio](diagnostic-data-collection.md)
* [Možnosti zpětné vazby v aplikaci Visual Studio](../ide/feedback-options.md)
* [Nahlášení problému se sadou Visual Studio](../ide/how-to-report-a-problem-with-visual-studio.md)
* [Komunita vývojářů sady Visual Studio](https://aka.ms/feedback/suggest?space=8)
* [Prohlášení společnosti Microsoft o zásadách ochrany osobních údajů](https://privacy.microsoft.com/privacystatement)
