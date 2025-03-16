# Angular Workshop: Routing with parameters


https://github.com/user-attachments/assets/d9c85b72-cf19-4f39-91d8-92b95a1bfd90


In this task, you'll create a `ClashDetailsComponent`. You'll navigate from the `ClashListComponent` to the `ClashDetailsComponent` by clicking on a `routerLink` in the (already existing) `BookCardComponent` (child of the `ClashListComponent`). You'll pass the `clash-id` as a parameter.

---

### **1. Create the _ClashDetailComponent_**

```ts
ng generate component clash/clash-detail
```

#### `clash-detail.component.ts`:

Add a `clashId = input('')` to `ClashDetailComponent`

#### `clash-detail.component.html`:

For now, you can leave it like it is. We'll focus on the template later.

---

### **2. Create the routing configuration**

#### `app.config.ts`:

Add a configuration that allows us to receive routing parameters directly as component inputs:

```ts
export const appConfig: ApplicationConfig = {
  providers: [
    // ...
    provideRouter(routes, withComponentInputBinding()),
    // ...
  ],
};
```

#### `app.routes.ts`:

```ts
{
  path: 'clashes/:clashId',
  component: ClashDetailComponent,
}
```

---

### **3. Add a `routerLink` to the `ClashCardComponent`**

If done, you can test your navigation setup.

---

### **4. Receive the `clashId` navigation parameter**

Everything is set-up for receiving the navigation parameter `clashId` via input.

```html
<h3 class="text-xl font-bold">Clash ({{ clashId() }})</h3>
```

Add a `routerLink` for navigating back.

---

### **5. Load the `Clash` by `clashId`**

1. Add a `findById(clashId: string): Observable<Clash>` method to the `ClashService`.
2. Inject the `ClashService` into the `ClashDetailComponent`.
3. Introduce a `clash = signal<Clash | null>(null)` in your `ClashDetailComponent`.
4. Use a [effect](https://angular.dev/guide/signals#effects) to load the clash.

---

### **6. Implement the `clash-detail.component.html`**
