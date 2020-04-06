---
title: 'Postup: Správa více vláken ve spravovaném kódu | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 59730063-cc29-4dae-baff-2234ad8d0c8f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ceaa0af4f57fe374cf9cf4b2dd8b4f40af74a852
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702783"
---
# <a name="how-to-manage-multiple-threads-in-managed-code"></a>Postup: Správa více vláken ve spravovaném kódu
Pokud máte spravované rozšíření VSPackage, které volá asynchronní metody nebo má operace, které se provádějí v jiných vláknech než ve vlákně uživatelského rozhraní sady Visual Studio, postupujte podle pokynů uvedených níže. Vlákno uživatelského rozhraní můžete zachovat tak, aby reagovalo, protože nemusí čekat na dokončení práce na jiném vlákně. Můžete zefektivnit váš kód, protože nemáte další vlákna, která zabírají místo zásobníku a můžete jej spolehlivější a snadněji ladit, protože se vyhnete zablokování a zablokuje.

 Obecně můžete přepnout z vlákna uživatelského rozhraní na jiné vlákno nebo naopak. Když metoda vrátí, aktuální vlákno je vlákno, ze kterého byl původně volán.

> [!IMPORTANT]
> Následující pokyny používají api v <xref:Microsoft.VisualStudio.Threading> oboru názvů, zejména <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> třídy. Api v tomto oboru názvů [!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)]jsou nové v . Můžete získat instanci <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> a <xref:Microsoft.VisualStudio.Shell.ThreadHelper> `ThreadHelper.JoinableTaskFactory`z vlastnosti .

## <a name="switch-from-the-ui-thread-to-a-background-thread"></a>Přepnutí z vlákna uživatelského rozhraní na vlákno na pozadí

1. Pokud jste ve vlákně uživatelského rozhraní a chcete provést asynchronní `Task.Run()`práci na vlákně na pozadí, použijte :

    ```csharp
    await Task.Run(async delegate{
        // Now you're on a separate thread.
    });
    // Now you're back on the UI thread.

    ```

2. Pokud jste ve vlákně uživatelského rozhraní a chcete synchronně blokovat při provádění práce na <xref:System.Threading.Tasks.TaskScheduler> `TaskScheduler.Default` vlákně na pozadí, použijte vlastnost uvnitř <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A>:

    ```csharp
    // using Microsoft.VisualStudio.Threading;
    ThreadHelper.JoinableTaskFactory.Run(async delegate {
        await TaskScheduler.Default;
        // You're now on a separate thread.
        DoSomethingSynchronous();
        await OrSomethingAsynchronous();
    });
    ```

## <a name="switch-from-a-background-thread-to-the-ui-thread"></a>Přepnutí z vlákna na pozadí do vlákna uživatelského rozhraní

1. Pokud jste ve vlákně na pozadí a chcete něco udělat <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>ve vlákně uživatelského rozhraní, použijte :

    ```csharp
    // Switch to main thread
    await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();
    ```

     Tuto metodu <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> můžete použít k přepnutí do vlákna uživatelského rozhraní. Tato metoda odešle zprávu vlákno uživatelského rozhraní s pokračováním aktuální asynchronní metody a také komunikuje se zbytkem architektury podprocesu nastavit správnou prioritu a vyhnout se zablokování.

     Pokud vaše metoda vlákna na pozadí není asynchronní a nelze ji asynchronní, `await` můžete stále použít syntaxi k přepnutí do vlákna uživatelského rozhraní zabalením práce s <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A>, jako v tomto příkladu:

    ```csharp
    ThreadHelper.JoinableTaskFactory.Run(async delegate {
        // Switch to main thread
        await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();
        // Do your work on the main thread here.
    });
    ```
