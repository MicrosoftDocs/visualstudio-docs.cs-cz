---
title: Načtení informací o řetězci dotazu v online aplikaci ClickOnce
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, query strings
- query strings, retrieving information
ms.assetid: 48ce098a-a075-481b-a5f5-c8ba11f63120
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 30169a43d88f0ee8ae2c428e5a3da0aef0b9d642
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72637865"
---
# <a name="how-to-retrieve-query-string-information-in-an-online-clickonce-application"></a>Postupy: načtení informací řetězce dotazu v online aplikaci ClickOnce
*Řetězec dotazu* je část adresy URL začínající otazníkem (?), která obsahuje libovolné informace ve tvaru *název = hodnota*. Předpokládejme, že máte aplikaci [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] s názvem `WindowsApp1`, kterou hostuje `servername`, a chcete předat hodnotu pro proměnnou `username` při spuštění aplikace. Adresa URL může vypadat takto:

 `http://servername/WindowsApp1.application?username=joeuser`

 Následující dva postupy ukazují, jak použít [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikaci k získání informací o řetězci dotazu.

> [!NOTE]
> Informace v řetězci dotazu můžete předávat jenom v případě, že se aplikace spouští pomocí protokolu HTTP namísto použití sdílené složky nebo místního systému souborů.

 První postup ukazuje, jak může vaše aplikace [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] použít malý kód ke čtení těchto hodnot při spuštění aplikace.

 Následující postup ukazuje, jak nakonfigurovat aplikaci [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] pomocí nástroje MageUI. exe tak, aby mohla přijmout parametry řetězce dotazu. To je nutné provést při každém publikování aplikace.

> [!NOTE]
> V části zabezpečení níže v tomto tématu se můžete rozhodnout, že tuto funkci povolíte.

 Informace o tom, jak vytvořit [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nasazení pomocí nástroje *Mage. exe* nebo *MageUI. exe*, naleznete v tématu [Návod: Ruční nasazení aplikace ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).

> [!NOTE]
> Počínaje verzí .NET Framework 3,5 SP1 je možné předat argumenty příkazového řádku do offline aplikace [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. Chcete-li zadat argumenty do aplikace, můžete předat parametry do souboru zástupce pomocí. Rozšíření APPREF-MS.

### <a name="to-obtain-query-string-information-from-a-clickonce-application"></a>Získání informací o řetězci dotazu z aplikace ClickOnce

1. Do projektu vložte následující kód. Aby tento kód fungoval, bude nutné mít odkaz na System. Web a přidat `using` nebo `Imports` direktivy pro System. Web, System. Collections. Specialized a System. Deployment. Application.

     [!code-csharp[ClickOnceQueryString#1](../deployment/codesnippet/CSharp/how-to-retrieve-query-string-information-in-an-online-clickonce-application_1.cs)]
     [!code-vb[ClickOnceQueryString#1](../deployment/codesnippet/VisualBasic/how-to-retrieve-query-string-information-in-an-online-clickonce-application_1.vb)]

2. Voláním dříve definované funkce načtěte <xref:System.Collections.DictionaryBase.Dictionary%2A> parametrů řetězce dotazu indexovaného podle názvu.

### <a name="to-enable-query-string-passing-in-a-clickonce-application-with-mageuiexe"></a>Povolení předávání řetězců dotazů v aplikaci ClickOnce pomocí MageUI. exe

1. Otevřete příkazový řádek .NET a zadejte:

   ```cmd
   MageUI
   ```

2. V nabídce **soubor** vyberte možnost **otevřít**a otevřete manifest nasazení aplikace [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], což je soubor končící příponou `.application`.

3. V levém navigačním okně vyberte panel **Možnosti nasazení** a zaškrtněte políčko **povoluje předání parametrů adresy URL do aplikace** .

4. V nabídce **soubor** vyberte **Uložit**.

> [!NOTE]
> Alternativně můžete povolit předávání řetězců dotazu v [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]. Zaškrtněte políčko **Allow URL Parameters Passed to Application** , které lze najít otevřením **vlastností projektu**, výběrem karty **publikovat** , kliknutím na tlačítko **Možnosti** a následným výběrem **Manifests**.

## <a name="robust-programming"></a>Robustní programování
 Při použití parametrů řetězce dotazu musíte pečlivě zvážit, jak je vaše aplikace nainstalovaná a aktivovaná. Pokud je vaše aplikace nakonfigurovaná tak, aby se nainstalovala na počítač uživatele z webu nebo ze sdílené síťové složky, může uživatel aplikaci aktivovat jenom jednou přes adresu URL. Potom bude uživatel obvykle aktivovat vaši aplikaci pomocí zástupce v nabídce **Start** . V důsledku toho je zaručeno, že aplikace získá argumenty řetězce dotazu pouze jednou během své životnosti. Pokud se rozhodnete tyto argumenty uložit v počítači uživatele pro budoucí použití, zodpovídáte za jejich uložení bezpečným a bezpečným způsobem.

 Pokud je vaše aplikace online, bude vždy aktivována prostřednictvím adresy URL. I v tomto případě musí být aplikace zapsána, aby fungovala správně, pokud parametry řetězce dotazu chybí nebo jsou poškozené.

## <a name="net-framework-security"></a>zabezpečení v rozhraní .NET Framework
 Povolte předávání parametrů adresy URL vaší [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikaci pouze v případě, že plánujete před použitím vyčistit vstup všech škodlivých znaků. Řetězec, který je vložený pomocí uvozovek, lomítka nebo středníků, může například provádět libovolné operace s daty, pokud se používá nefiltrovaný dotaz SQL na databázi. Další informace o zabezpečení řetězce dotazů najdete v tématu [Přehled zneužití skriptů](https://msdn.microsoft.com/Library/772c7312-211a-4eb3-8d6e-eec0aa1dcc07).

## <a name="see-also"></a>Viz také:
- [Zabezpečené aplikace ClickOnce](../deployment/securing-clickonce-applications.md)
