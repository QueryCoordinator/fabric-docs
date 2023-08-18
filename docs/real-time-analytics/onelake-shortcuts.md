---
title: Create OneLake shortcuts in Real-Time Analytics
description: Learn how to create a OneLake shortcut to query data from internal and external sources.
ms.reviewer: tzgitlin
ms.author: yaschust
author: YaelSchuster
ms.topic: how-to
ms.custom: build-2023
ms.date: 08/15/2023
ms.search.form: product-kusto
---

# Create OneLake shortcuts

[!INCLUDE [preview-note](../includes/preview-note.md)]

OneLake is a single, unified, logical data lake for [!INCLUDE [product-name](../includes/product-name.md)] to store lakehouses, warehouses, KQL databases, and other items. Shortcuts are embedded references within OneLake that point to other files' store locations without moving the original data. The embedded reference makes it appear as though the files and folders are stored locally but in reality; they exist in another storage location. Shortcuts can be updated or removed from your items, but these changes don't affect the original data and its source. For more information, see [OneLake shortcuts](../onelake/onelake-shortcuts.md).

In this article, you learn how to create a OneLake shortcut from internal and external sources to query your data in Real-Time Analytics. Select the desired tab that corresponds with the shortcut you'd like to create.

> [!NOTE]
> Use OneLake shortcuts when you want to infrequently run queries on historical data without partitioning or indexing the data.
> If you want to run queries frequently and accelerate performance, import the data directly into your KQL database.

## [OneLake shortcut](#tab/onelake-shortcut)

[!INCLUDE [onelake-shortcut-prerequisites](../includes/real-time-analytics/onelake-shortcut-prerequisites.md)]

1. Browse to an existing KQL database.
1. Select **New** > **OneLake shortcut**.

    :::image type="content" source="media/onelake-shortcuts/onelake-shortcut/home-tab.png" alt-text="Screenshot of the Home tab showing the dropdown of the New button. The option titled OneLake shortcut is highlighted.":::

[!INCLUDE [onelake-shortcut](../includes/onelake-shortcut.md)]

## [Azure Data Lake Storage Gen2](#tab/adlsgen2)

[!INCLUDE [adlsgen2-prerequisites](../includes/real-time-analytics/adlsgen2-prerequisites.md)]

1. Browse to an existing KQL database.
1. Select **New** > **OneLake shortcut**.

    :::image type="content" source="media/onelake-shortcuts/onelake-shortcut/home-tab.png" alt-text="Screenshot of the Home tab showing the dropdown of the New button. The option titled OneLake shortcut is highlighted.":::

[!INCLUDE [adls-gen2-shortcut](../includes/adls-gen2-shortcut.md)]

## [Amazon S3](#tab/amazon-s3)

[!INCLUDE [amazons3-prerequisites](../includes/real-time-analytics/amazons3-prerequisites.md)]

1. Browse to an existing KQL database.
1. Select **New** > **OneLake shortcut**.

    :::image type="content" source="media/onelake-shortcuts/onelake-shortcut/home-tab.png" alt-text="Screenshot of the Home tab showing the dropdown of the New button. The option titled OneLake shortcut is highlighted.":::

[!INCLUDE [amazon-s3-shortcut](../includes/amazon-s3-shortcut.md)]

---

The database refreshes automatically. The shortcut appears under **Shortcuts** in the **Data tree**.

:::image type="content" source="media/onelake-shortcuts/azure-data-lake-storage-gen2-shortcut/data-tree.png" alt-text="Screenshot of the data tree showing the new shortcut.":::

The OneLake shortcut has been created. You can now query this data.

## Query data

To query data from the OneLake shortcut, use the [`external_table()` function](/azure/data-explorer/kusto/query/externaltablefunction?context=/fabric/context/context).

1. On the rightmost side of your database, select **Check your data**. The window opens with a few example queries you can run to get an initial look at your data.
1. Replace the table name placeholder with `external_table('`*Shortcut name*`')`.
1. Select **Run** or press **Shift+ Enter** to run a selected query.

:::image type="content" source="media/onelake-shortcuts/amazon-s3-shortcut/query-shortcut.png" alt-text="Screenshot of the check your data window showing the results of an example query."  lightbox="media/onelake-shortcuts/amazon-s3-shortcut/query-shortcut.png":::

## Next steps

* [Query data in a KQL queryset](kusto-query-set.md)
* [`external_table()` function](/azure/data-explorer/kusto/query/externaltablefunction?context=/fabric/context/context)
