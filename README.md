# Multer en Ionic

> npm install -g ionic

En este ejemplo utilizo ionic para guardar imagenes en el servidor de express.

Se hizo un servicio de subida quedando el servicio o la peticion de esta manera

```javascript
uploadImage(title: string, description: string, photo: File) {
    const fd = new FormData();
    fd.append('title', title);
    fd.append('description', description);
    fd.append('image', photo);
    return this.http.post(`${URL}/inicial/crear`, fd);
  }
```
Esto permitira que se pida una petición post y los requerimientos en este caso un titulo, una descripción y una archivo a subir.

Despúes en el componente home.ts
se hacer una metodo de cambio (change) para ver el cambio de archivo que se va subir al igual que una vista previa

```typescript
onPhotoSelected(event): void {
    if (event.target.files && event.target.files[0]) {
      this.file = <File>event.target.files[0];
      // image preview
      const reader = new FileReader();
      reader.onload = e => this.photoSelected = reader.result;
      reader.readAsDataURL(this.file);
    }
```

