---
title: 'Postupy: Správa více vláken ve spravovaném kódu | Microsoft Docs'
description: Naučte se spravovat více vláken v kódu, pokud vaše spravovaná rozšíření VSPackage volá asynchronní metody nebo obsahuje operace ve vláknu uživatelského rozhraní sady Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 59730063-cc29-4dae-baff-2234ad8d0c8f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7b301770a54baf0416aa9fcc838a9a6633252fbe
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105073128"
---
# <a name="how-to-manage-multiple-threads-in-managed-code"></a>Postupy: Správa více vláken ve spravovaném kódu
Máte-li spravované rozšíření VSPackage, které volá asynchronní metody nebo obsahuje operace spouštěné v jiných vláknech než ve vlákně uživatelského rozhraní sady Visual Studio, měli byste postupovat podle pokynů uvedených níže. Vlákno uživatelského rozhraní lze nechat reagovat, protože nemusí čekat na dokončení práce na jiném vlákně. Svůj kód můžete zefektivnit, protože nemáte další vlákna, která zabírají místo v zásobníku, a můžete ho spolehlivější a jednodušší ladit, protože se vyhnete zablokování a nereagující se na kód.

 Obecně můžete přepnout z vlákna uživatelského rozhraní do jiného vlákna nebo naopak. Když se metoda vrátí, aktuální vlákno je vlákno, ze kterého bylo původně voláno.

> [!IMPORTANT]
> Následující pokyny používají rozhraní API v <xref:Microsoft.VisualStudio.Threading> oboru názvů, zejména <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> třídy. Rozhraní API v tomto oboru názvů jsou v nástroji novinkou [!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)] . Můžete získat instanci <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> z <xref:Microsoft.VisualStudio.Shell.ThreadHelper> vlastnosti `ThreadHelper.JoinableTaskFactory` .

## <a name="switch-from-the-ui-thread-to-a-background-thread"></a>Přepnutí z vlákna uživatelského rozhraní do vlákna na pozadí

1. Pokud jste ve vlákně uživatelského rozhraní a chcete provést asynchronní práci ve vlákně na pozadí, použijte `Task.Run()` :

    ```csharp
    await Task.Run(async delegate{
        // Now you're on a separate thread.
    });
    // Now you're back on the UI thread.

    ```

2. Pokud jste ve vlákně uživatelského rozhraní a chcete synchronně blokovat při práci na vlákně na pozadí, použijte <xref:System.Threading.Tasks.TaskScheduler> vlastnost `TaskScheduler.Default` uvnitř <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A> :

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

1. Pokud se nacházíte ve vlákně na pozadí a chcete něco udělat ve vlákně uživatelského rozhraní, použijte <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> :

    ```csharp
    // Switch to main thread
    await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();
    ```

     Můžete použít <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> metodu pro přepnutí do vlákna uživatelského rozhraní. Tato metoda odesílá zprávu do vlákna uživatelského rozhraní s pokračováním aktuální asynchronní metody a také komunikuje se zbytkem rozhraní pro dělení na vlákna, aby nastavila správnou prioritu a zabránila zablokování.

     Pokud vaše metoda vlákna na pozadí není asynchronní a nemůžete ji učinit asynchronní, můžete i nadále použít `await` syntaxi pro přepnutí do vlákna uživatelského rozhraní, a to tak, že zabalíte svou práci s <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A> , jako v tomto příkladu:

    ```csharp
    ThreadHelper.JoinableTaskFactory.Run(async delegate {
        // Switch to main thread
        await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();
        // Do your work on the main thread here.
    });
    ```
