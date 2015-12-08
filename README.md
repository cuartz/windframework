# windframework



			for (String retainedObject:wm.retainedObjects()){
			
				
				Field field=instancedPage.getClass().getDeclaredField(retainedObject);//field.set(instancedPage,  mapper.readValue(actualObj.traverse(), field.getType()));//class););
				field.setAccessible(true);
				jsonResponse=jsonResponse+"\""+field.getName()+"\":"+mapper.writeValueAsString(field.get(instancedPage))+",";
				WindSpace2 wSAnnotation=field.getAnnotation(WindSpace2.class);
				if (wSAnnotation.alive() && WindEntity.class.isAssignableFrom(field.getType())){//field.get(pageClass) instanceof WindEntity){
					

					wService2.notifyChange((WindEntity)field.get(instancedPage));
				}
				
			}
